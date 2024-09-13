---
title: EMC-2 Sample Data Set
subtitle: A synthetic, narrative-driven alternative to Enron data
author: John Benson
author-url: "https://john-benson.com"
date: 2024-09-12
lang: en
toc-title: Contents
version: v1.1
---

# EMC-2 Interactive Timeline

<div id="command-center">
    <div id="filters">
        <h2>Filters</h2>
        <select id="participantFilter">
            <option value="">All Participants</option>
        </select>
        <select id="eventTypeFilter">
            <option value="">All Event Types</option>
        </select>
        <input type="date" id="startDate">
        <input type="date" id="endDate">
        <button id="applyDateFilter">Apply Date Filter</button>
        <button id="resetFilters">Reset Filters</button>
    </div>
    <div id="timeline"></div>
    <div id="details">
        <h2>Event Details</h2>
        <div id="event-details"></div>
    </div>
</div>

<style>
  
:root {
    --font-family: "Berkeley Mono", "JetBrains Mono", monospace;
    --line-height: 1.4rem;
    --border-thickness: 1px;
    --text-color: #fa3;
    --background-color: #222;
}

body, select, button, input {
    font-family: var(--font-family);
    line-height: var(--line-height);
    color: var(--text-color);
    background-color: var(--background-color);
    margin: 0;
    padding: 0;
}

body {
    padding: 20px;
    overflow-x: hidden;
}

#command-center {
    display: grid;
    grid-template-columns: 180px 1fr 250px;
    gap: 20px;
    height: 90vh;
}

#filters {
    grid-column: 1;
    border-right: var(--border-thickness) solid var(--text-color);
    padding-right: 15px;
}

#timeline {
    grid-column: 2;
    overflow-y: auto;
    border: var(--border-thickness) solid var(--text-color);
    padding: 15px;
}

#details {
    grid-column: 3;
    border-left: var(--border-thickness) solid var(--text-color);
    padding-left: 15px;
    overflow-y: auto;
}

h1, h2 {
    color: var(--highlight-color);
    margin: 0 0 15px 0;
}

h1 {
    font-size: 1.8rem;
    margin-bottom: 30px;
}

h2 {
    font-size: 1.4rem;
}

select, button, input {
    width: 100%;
    margin-bottom: 15px;
    border: var(--border-thickness) solid var(--text-color);
    padding: 8px;
    font-size: 0.9rem;
}

.event {
    border: var(--border-thickness) solid var(--text-color);
    margin-bottom: 10px;
    padding: 10px;
    cursor: pointer;
    font-size: 1rem;
}

.event:hover {
    background-color: rgba(255, 255, 102, 0.1);
}

.event-time {
    color: var(--highlight-color);
    font-weight: bold;
}

#event-details {
    border: var(--border-thickness) solid var(--text-color);
    padding: 15px;
    margin-top: 15px;
    font-size: 0.9rem;
}
</style>

<script src="https://cdnjs.cloudflare.com/ajax/libs/moment.js/2.29.1/moment.min.js"></script>
  <script>
        const events = [
            {
                date: "1995-08-17T23:59:00",
                participants: ["Eugene Belford"],
                type: "Email",
                title: "Eugene emails Phantom Phreak",
                description: "Eugene begins enlisting help for his plan involving the Gibson supercomputer. Email is encrypted using ROT13 cipher."
            },
            {
                date: "1995-08-24",
                participants: ["Sarah Chen"],
                type: "Report",
                title: "Network Traffic Analysis Report",
                description: "Sarah Chen prepares a report observing suspicious activities between August 15 and August 23, identifying potential unauthorized access to the Gibson supercomputer."
            },
            {
                date: "1995-09-05",
                participants: ["Zero Cool", "Acid Burn", "Phantom Phreak", "Cereal Killer", "Lord Nikon"],
                type: "Chat",
                title: "Hackers' Group Chat",
                description: "Hackers discuss recent activities and plan to explore new targets, unaware of the larger conspiracy."
            },
            {
                date: "1995-09-10",
                participants: ["Agent Richard Gill"],
                type: "Memo",
                title: "FBI Internal Memorandum",
                description: "Agent Gill reports on initial investigation into cyber attacks affecting corporations, including Ellingson Mineral Company."
            },
            {
                date: "1995-09-15",
                participants: ["Eugene Belford"],
                type: "Communication",
                title: "Intercepted Communication",
                description: "Eugene discusses escalating plans and evading authorities with an unknown associate."
            },
            {
                date: "1995-09-20",
                participants: ["Ellingson Employees"],
                type: "Internal Messages",
                title: "Employee Concerns",
                description: "Ellingson employees express concerns over system anomalies and rumors about 'The Plague' circulate."
            },
            {
                date: "1995-09-25",
                participants: ["CyberShield Security Solutions"],
                type: "Analysis",
                title: "Da Vinci Virus Analysis",
                description: "External security firm completes technical analysis of the Da Vinci virus for Ellingson, confirming its sophistication."
            },
            {
                date: "1995-10-02",
                participants: ["Eugene Belford"],
                type: "Email",
                title: "Routine Security Update",
                description: "Eugene announces he will be out of the office and assigns tasks to team members."
            },
            {
                date: "1995-10-04",
                participants: ["Eugene Belford", "Margo Wallace"],
                type: "Email",
                title: "Project Da Vinci",
                description: "Eugene confirms the virus is ready and coordinates timing for deployment with Margo."
            },
            {
                date: "1995-10-06",
                participants: ["Eugene Belford", "Hal Benson"],
                type: "Request",
                title: "Additional Security Budget",
                description: "Eugene requests additional security budget and proposes upgrades to the Gibson supercomputer."
            },
            {
                date: "1995-10-08",
                participants: ["Phantom Phreak", "Eugene Belford"],
                type: "Communication",
                title: "Hacker Collaboration",
                description: "Phantom Phreak agrees to participate in Eugene's plan involving the Gibson."
            },
            {
                date: "1995-10-10T11:15:00",
                participants: ["Eugene Belford", "Hal Benson", "HR", "Sarah Chen"],
                type: "Email",
                title: "Eugene's Resignation",
                description: "Eugene submits his resignation, effective October 15, surprising management."
            },
            {
                date: "1995-10-12",
                participants: ["Eugene Belford", "Phantom Phreak"],
                type: "Communication",
                title: "Final Preparations",
                description: "Eugene and Phantom Phreak discuss final details for virus deployment."
            },
            {
                date: "1995-10-14",
                participants: ["TechWeekly Newsletter"],
                type: "Publication",
                title: "Industry Updates",
                description: "TechWeekly publishes an article on the increasing importance of cybersecurity in corporations."
            },
            {
                date: "1995-10-16T09:15:00",
                participants: ["Margo Wallace", "Operations Team"],
                type: "Report",
                title: "Weekly Operations Report",
                description: "Margo notes unusual patterns in oil tanker routes and requests investigation into anomalies."
            },
            {
                date: "1995-10-17T14:30:00",
                participants: ["Margo Wallace", "Eugene Belford"],
                type: "Communication",
                title: "Cover Story Confirmation",
                description: "Margo confirms the 'routine maintenance' cover story is in place but expresses concern about timing."
            },
            {
                date: "1995-10-18",
                participants: ["Zero Cool", "Acid Burn", "Cereal Killer", "Lord Nikon"],
                type: "Chat",
                title: "Hackers Discover Anomalies",
                description: "Hackers discuss unusual findings on the Gibson supercomputer and plan to investigate further."
            },
            {
                date: "1995-10-19T08:30:00",
                participants: ["Sarah Chen", "IT Team"],
                type: "Alert",
                title: "Unusual Activity Detected",
                description: "Sarah Chen detects unusual activity on the Gibson and urges immediate investigation."
            },
            {
                date: "1995-10-19T09:00:00",
                participants: ["Hal Benson", "Board of Directors"],
                type: "Meeting",
                title: "Emergency Board Meeting Scheduled",
                description: "Hal schedules an emergency board meeting for October 20 to discuss cyber attack response."
            },
            {
                date: "1995-10-19T10:45:00",
                participants: ["Sarah Chen", "Hal Benson"],
                type: "Report",
                title: "Initial Virus Analysis",
                description: "Sarah reports initial analysis of the 'Da Vinci' virus to Hal, recommending involvement of law enforcement."
            },
            {
                date: "1995-10-19T11:30:00",
                participants: ["Sarah Chen", "Hal Benson"],
                type: "Update",
                title: "System Status Update",
                description: "Sarah provides update on system status, noting that the Gibson is compromised but isolated."
            },
            {
                date: "1995-10-19T13:20:00",
                participants: ["Eugene Belford", "Margo Wallace"],
                type: "Communication",
                title: "Virus Activation Confirmation",
                description: "Eugene confirms everything is in place for the virus activation at midnight."
            },
            {
                date: "1995-10-19T14:30:00",
                participants: ["Paul Jenkins", "Tim Silent", "Sarah Chen"],
                type: "Report",
                title: "Strange Behavior in Data Center",
                description: "IT staff report strange behavior in the data center, including 'skull' graphics appearing on screens."
            },
            {
                date: "1995-10-19T15:55:00",
                participants: ["Sarah Chen", "FBI Cybercrime Division"],
                type: "Request",
                title: "FBI Assistance Request",
                description: "Sarah formally requests FBI assistance in investigating the cyber attack."
            },
            {
                date: "1995-10-19T16:45:00",
                participants: ["PR Team", "Legal Team"],
                type: "Preparation",
                title: "PR and Legal Strategy",
                description: "PR and Legal teams prepare press releases and analyze potential legal implications of the cyber attack."
            },
            {
                date: "1995-10-20T00:00:00",
                participants: [],
                type: "Attack",
                title: "Da Vinci Virus Activates",
                description: "The Da Vinci virus activates, causing widespread system disruptions at Ellingson. Oil tanker routing systems are compromised, and strange 3D skull graphics appear on systems."
            },
            {
                date: "1995-10-20T02:30:00",
                participants: ["Sarah Chen", "Hal Benson"],
                type: "Update",
                title: "Urgent Virus Situation Update",
                description: "Sarah provides urgent updates on the virus situation, noting it has breached secondary firewalls and evidence points to insider involvement."
            },
            {
                date: "1995-10-20T08:30:00",
                participants: ["Margo Wallace", "Eugene Belford"],
                type: "Communication",
                title: "Concerns Over Exposure",
                description: "Margo reports systems acting up and expresses concern over the accelerated timeline to Eugene."
            },
            {
                date: "1995-10-20T09:15:00",
                participants: ["HR Director", "Hal Benson"],
                type: "Report",
                title: "Employee Data Compromise",
                description: "HR reports potential compromise of employee personal data, including names, addresses, and Social Security numbers."
            },
            {
                date: "1995-10-20T10:30:00",
                participants: ["Sarah Chen", "Hal Benson"],
                type: "Action",
                title: "Eugene's Access Revoked",
                description: "Sarah revokes Eugene's access credentials and conducts an audit of his recent system activities, finding he accessed restricted areas before the attack."
            }
        ];

        const timeline = document.getElementById('timeline');
        const eventDetails = document.getElementById('event-details');
        const participantFilter = document.getElementById('participantFilter');
        const eventTypeFilter = document.getElementById('eventTypeFilter');
        const startDateFilter = document.getElementById('startDate');
        const endDateFilter = document.getElementById('endDate');
        const applyDateFilterButton = document.getElementById('applyDateFilter');
        const resetFiltersButton = document.getElementById('resetFilters');

        function populateFilters() {
            const participants = [...new Set(events.flatMap(e => e.participants))];
            const eventTypes = [...new Set(events.map(e => e.type))];

            participants.forEach(p => {
                const option = document.createElement('option');
                option.value = p;
                option.textContent = p;
                participantFilter.appendChild(option);
            });

            eventTypes.forEach(t => {
                const option = document.createElement('option');
                option.value = t;
                option.textContent = t;
                eventTypeFilter.appendChild(option);
            });

            // Set initial date range
            const dates = events.map(e => new Date(e.date));
            startDateFilter.value = moment(Math.min(...dates)).format('YYYY-MM-DD');
            endDateFilter.value = moment(Math.max(...dates)).format('YYYY-MM-DD');
        }

function showEvents() {
            const selectedParticipant = participantFilter.value;
            const selectedType = eventTypeFilter.value;
            const startDate = new Date(startDateFilter.value);
            const endDate = new Date(endDateFilter.value);
            endDate.setHours(23, 59, 59); // Include the entire end date
        
            const filteredEvents = events.filter(e => {
                const eventDate = new Date(e.date);
                return (selectedParticipant === '' || e.participants.includes(selectedParticipant)) &&
                       (selectedType === '' || e.type === selectedType) &&
                       (eventDate >= startDate && eventDate <= endDate);
            });
        
            timeline.innerHTML = '';
            filteredEvents.forEach(event => {
                const eventElement = document.createElement('div');
                eventElement.className = 'event';
                eventElement.innerHTML = `
                    <span class="event-time">[${moment(event.date).format('YYYY-MM-DD HH:mm')}]</span>
                    <strong>${event.title}</strong> (${event.type})
                `;
                eventElement.onclick = () => showEventDetails(event);
                timeline.appendChild(eventElement);
            });
        }
        
        function showEventDetails(event) {
            eventDetails.innerHTML = `
                <h3>${event.title}</h3>
                <p><strong>Date:</strong> ${moment(event.date).format('MMMM D, YYYY HH:mm')}</p>
                <p><strong>Participants:</strong> ${event.participants.join(', ') || 'None specified'}</p>
                <p><strong>Type:</strong> ${event.type}</p>
                <p><strong>Description:</strong> ${event.description}</p>
            `;
        }
        
        participantFilter.onchange = showEvents;
        eventTypeFilter.onchange = showEvents;
        applyDateFilterButton.onclick = showEvents;
        resetFiltersButton.onclick = () => {
            participantFilter.value = '';
            eventTypeFilter.value = '';
            const dates = events.map(e => new Date(e.date));
            startDateFilter.value = moment(Math.min(...dates)).format('YYYY-MM-DD');
            endDateFilter.value = moment(Math.max(...dates)).format('YYYY-MM-DD');
            showEvents();
        };
        
        populateFilters();
        showEvents();
        
    </script>