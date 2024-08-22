<script setup>
import { computed, onMounted } from 'vue'
    const headers = ['Team', 'Day', 'Time', 'Hall'];
    const dataList = [
        {   
            id: 1,
            team: 'U8 mix',
            
            events: [
                {
                    day: 'Friday',
                    time: {
                        start: '15.30',
                        end: '16.45'
                    },
                    hall: 'Deusterschule Kitzingen',
                }
            ]
        },

        { 
            id: 2,
            team: 'U10 mix',
            events: [ 
                {
                    day: 'Friday',
                    time: {
                        start: '17.00',
                        end: '18.30'
                    },
                    hall: 'Deusterschule Kitzingen'
                },
                {
                    day: 'Friday',
                    time: {
                        start: '16.45',
                        end: '18.15'
                    },
                    hall: 'Deusterschule Kitzingen'
                }
            ]
           
        },

        { 
            id: 3,
            team: 'U12 mix',
            events: [
                {
                    day: 'Thursday',
                    time: {
                        start: '17.35',
                        end: '18.45'
                    },
                    hall: 'Mainstockheim',
                },

                {
                    day: 'Thursday',
                    time: {
                        start: '11.00',
                        end: '12.30'
                    },
                    hall: 'Mainstockheim'
                }
            ]
           
        },

        { 
            id: 4,
            team: 'U14 m',
            events: [
                {
                    day: 'Thursday',
                    time: {
                        start: '16.30',
                        end: '18.30'
                    },
                    hall: 'Arena Kitzingen',
                },
                {
                    day: 'Thursday',
                    time: {
                        start: '17.00',
                        end: '18.30'
                    },
                    hall: 'Arena Kitzingen'
                }
            ]
        },
        { 
            id: 5,
            team: 'U14 w',
            events: [
                {
                    day: 'Thursday',
                    time: {
                        start: '17.00',
                        end: '18.30'
                    },
                    hall: 'Arena Kitzingen',
                },
                {
                    day: 'Thursday',
                    time: {
                        start: '18.30',
                        end: '20.30'
                    },
                    hall: 'Arena Kitzingen'
                }
            ]
        },

        { 
            id: 6,
            team: 'U16 m',
            events: [
                {
                    day: 'Thursday',
                    time: {
                        start: '16.30',
                        end: '18.30'
                        
                    },
                    hall: 'Arena Kitzingen',
                },
                {
                    day: 'Thursday',
                    time: {
                        start: '18.30',
                        end: '20.00'
                    },
                    hall: 'Arena Kitzingen'
                }
            ]
        },

        { 
            id: 7,
            team: 'U18/20 Damon',
            
            events: [
                {
                    day: 'Thursday',
                    time: {
                        start: '18.30',
                        end: '20.00'
                    },
                    hall: 'Arena Kitzingen'
                }, 
                {
                    day: 'Thursday',
                    time: {
                        start: '18.30',
                        end: '20.30'
                    },
                    hall: 'Arena Kitzingen'
                }
            ]
        },

        { 
            id: 8,
            team: 'U20/Men',
            events: [
                {
                    day: 'Sunday',
                    time: {
                        start: '20.30',
                        end: '22.00'
                    },
                    hall: 'Arena Kitzingen'
                },
                {
                    day: 'Sunday',
                    time: {
                        start: '20.00',
                        end: '21.30'
                    },
                    hall: 'Arena Kitzingen'
                },
                {
                    day: 'Sunday',
                    time: {
                        start: '15.30',
                        end: '16.00'
                    },
                    hall: 'Arena Kitzingen'
                }
            ]
        },

        { 
            id: 9,
            team: 'OPEN COURT',
            events: [
                {
                    day: 'Sunday',
                    time: {
                        start: '15.30',
                        end: '16.00'
                    },
                    hall: 'Arena Kitzingen'
                }
            ]
        }
    ];

    const thStyle =  computed(() => (index) => {
        if (index === 2) {
            return { 'text-align': 'center'};
        } 
    });

    onMounted(() => {
        const tbody = document.querySelector('#table-data tbody');
        dataList.forEach( (entry, index) => {  
            //create a new currentRow
            let currentRow = document.createElement('tr');
            //create a cell for the current line and append it to the currentRow
            const tdTeam = document.createElement('td');
            tdTeam.textContent = entry.team;
            if (entry.events.length > 1) {
                tdTeam.setAttribute('rowspan', entry.events.length);
            }
            if (index %2 !== 0) {
                currentRow.classList.add('light-row')
            } else {
                currentRow.classList.add('dark-row')
            }
            currentRow.append(tdTeam);
            //for each events
            entry.events.forEach( (event, i) => {
                //if the index of the current event is > 0, commit the currentRow which already have data from the last row and create the new row
                if(i > 0) {
                    tbody.append(currentRow);
                    currentRow = document.createElement('tr');  
                    if (index %2 !== 0) {
                        currentRow.classList.add('light-row')
                    } else {
                        
                        currentRow.classList.add('dark-row')
                    }    
                }
                //create the tdDay for the event's day and append it to the currentRow
                const tdDay = document.createElement('td');
                tdDay.textContent = event.day;
                //create the tdTime for the event's time and append it to the currentRow
                const tdTime = document.createElement('td');
                tdTime.classList.add('time-td');
                //create and add stye for startTime div
                const divStartTime = document.createElement('div');
                divStartTime.textContent = event.time.start;
                divStartTime.classList.add('time-element')
                //create and add stye for endTime div
                const divEndTime = document.createElement('div');
                divEndTime.classList.add('time-element')
                divEndTime.textContent = event.time.end;
                const divDash = document.createElement('div');
                divDash.textContent = '-';
                // create div element to contain all time elements
                const divElement = document.createElement('div');
                divElement.classList.add('d-flex');
                divElement.append(divStartTime);
                divElement.append(divDash);
                divElement.append(divEndTime);
                // add divElement into tdTime
                tdTime.append(divElement);
                //create the tdHall for the event's hall and append it to the currentRow
                const tdHall = document.createElement('td');
                tdHall.textContent = event.hall;
                // check if is not last event add border-bottom
                if (i !== entry.events.length - 1) {
                    tdTime.classList.add('td-under-line');
                    tdHall.classList.add('td-under-line');
                    tdDay.classList.add('td-under-line');
                }
                currentRow.append(tdDay);  
                currentRow.append(tdTime);
                currentRow.append(tdHall);   
            });
            //append the currentRow to the table
            tbody.append(currentRow);
        })
    })
</script>

<template>
    <div class="container">
        <table id="table-data">
            <thead>
                <tr class="header-row">
                    <th v-for="(header, index) in headers" :style="thStyle(index)">
                      {{ header }}
                    </th>
                </tr>
            </thead>
            <tbody></tbody>
        </table>
    </div>
</template>

<style lang="scss">  
#table-data {
    min-width: 800px;
    /* 80% of 1440* */
    max-width: 1152px;  
    width: 80vw;
    border-collapse: collapse;

        tr {
        &.dark-row {
            background-color: #A9A9A9;
        }
        &.light-row {
            background-color: #C0C0C0;
        }
        &.header-row {
            border-bottom: 2px solid black !important;
            background-color: #ffff;
            th {
                text-align: left;
                padding-left: 2%;
            }
        }
        td {
            text-align: left;
            padding: 5px 0 5px 2%;
            &.td-under-line {
                border-bottom: 1px solid #a2a0a0 !important;
            }
            &.time-td {
                text-align: center;
                .time-element {
                    border-radius: 20px;
                    font-size: 14px;
                    background-color: #848884;
                    color: white;
                    width: 50px !important;
                    height: 20px;
                    margin: 0 10px 0 10px;
                    padding: 5px 2px 5px 2px;
                }
            }
        }
    }
}

.d-flex {
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
}

.container {
    padding: 10px;
    border: 1px solid  black;
}
</style>