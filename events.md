---
layout: page
title: Student Events
permalink: /events/
published: true
full-width: true
---

<style>
.events-page {
  max-width: 1080px;
  margin: 0 auto;
}

.events-intro {
  max-width: 720px;
  margin: 0 auto 2rem;
}

.events-intro p {
  margin-bottom: 0;
}

#events-calendar {
  margin: 0 auto 2.5rem;
  max-width: 900px;
  font-family: "Open Sans", "Helvetica Neue", Helvetica, Arial, sans-serif;
}

.events-actions {
  font-family: "Open Sans", "Noto Sans KR", "Apple SD Gothic Neo", "Malgun Gothic", Helvetica, Arial, sans-serif;
  margin: 0.75rem 0 0;
}

.fc .fc-button-primary {
  background-color: {{ site.link-col | default: "#008AFF" }};
  border-color: {{ site.link-col | default: "#008AFF" }};
}

.fc .fc-button-primary:hover,
.fc .fc-button-primary:focus {
  background-color: {{ site.hover-col | default: "#0085A1" }};
  border-color: {{ site.hover-col | default: "#0085A1" }};
}

.events-section {
  margin-top: 2.5rem;
}

.events-list {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 1rem;
  margin-top: 1rem;
}

.event-card {
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 1rem;
  background: #fff;
  font-family: "Open Sans", "Noto Sans KR", "Apple SD Gothic Neo", "Malgun Gothic", Helvetica, Arial, sans-serif;
}

.event-card h3 {
  margin-top: 0;
  margin-bottom: 0.5rem;
}

.event-details {
  padding: 0;
}

.event-details summary {
  cursor: pointer;
  display: block;
  list-style: none;
  padding: 1rem;
}

.event-details summary::-webkit-details-marker {
  display: none;
}

.event-summary-title {
  align-items: baseline;
  display: flex;
  gap: 0.75rem;
  justify-content: space-between;
}

.event-summary-title h3 {
  margin: 0;
}

.event-toggle {
  color: #777;
  font-family: "Open Sans", "Noto Sans KR", "Apple SD Gothic Neo", "Malgun Gothic", Helvetica, Arial, sans-serif;
  font-size: 1.25rem;
  line-height: 1;
}

.event-details[open] .event-toggle {
  transform: rotate(45deg);
}

.event-details-body {
  border-top: 1px solid #eee;
  padding: 0 1rem 1rem;
}

.event-meta {
  color: #666;
  font-family: "Open Sans", "Noto Sans KR", "Apple SD Gothic Neo", "Malgun Gothic", Helvetica, Arial, sans-serif;
  font-size: 0.95rem;
  margin: 0.25rem 0;
}

.event-description {
  margin: 0.75rem 0;
}

.events-empty {
  color: #666;
  font-style: italic;
}
</style>

<div class="events-page">
  <div class="events-intro">
    <p>Workshops, study sessions, talks, and other student-facing events.</p>
    <p class="events-actions">Import this calendar once, or subscribe by URL to receive updates when the event list changes.</p>
    <p class="events-actions"><a href="{{ '/events.ics' | relative_url }}">Subscribe / download calendar (.ics)</a></p>
  </div>

  <div id="events-calendar"></div>

{% if site.data.events %}
{% assign events = site.data.events | where: "status", "published" | sort: "date" %}
{% assign today = site.time | date: "%Y-%m-%d" %}

  <section class="events-section" aria-labelledby="upcoming-events">
    <h2 id="upcoming-events">Upcoming Events</h2>
    <div class="events-list">
{% assign upcoming_count = 0 %}
{% for event in events %}
{% assign event_date = event.date | date: "%Y-%m-%d" %}
{% if event_date >= today %}
{% assign upcoming_count = upcoming_count | plus: 1 %}
      <details class="event-card event-details">
        <summary>
          <div class="event-summary-title">
            <h3>{{ event.title }}</h3>
            <span class="event-toggle" aria-hidden="true">+</span>
          </div>
          <p class="event-meta">{{ event.date | date: "%B %-d, %Y" }}{% if event.time %}, {{ event.time }} KST{% endif %}</p>
        </summary>
        <div class="event-details-body">
{% if event.location %}
          <p class="event-meta">{{ event.location }}</p>
{% endif %}
{% if event.organizer %}
          <p class="event-meta">Organizer: {{ event.organizer }}</p>
{% endif %}
{% if event.description %}
          <p class="event-description">{{ event.description }}</p>
{% endif %}
{% if event.link %}
          <p><a href="{{ event.link }}">More information / RSVP</a></p>
{% endif %}
        </div>
      </details>
{% endif %}
{% endfor %}
{% if upcoming_count == 0 %}
      <p class="events-empty">No upcoming events are currently listed.</p>
{% endif %}
    </div>
  </section>

  <section class="events-section" aria-labelledby="past-events">
    <h2 id="past-events">Past Events</h2>
    <div class="events-list">
{% assign past_count = 0 %}
{% for event in events reversed %}
{% assign event_date = event.date | date: "%Y-%m-%d" %}
{% if event_date < today %}
{% assign past_count = past_count | plus: 1 %}
      <article class="event-card">
        <h3>{{ event.title }}</h3>
        <p class="event-meta">{{ event.date | date: "%B %-d, %Y" }}{% if event.time %}, {{ event.time }} KST{% endif %}</p>
{% if event.location %}
        <p class="event-meta">{{ event.location }}</p>
{% endif %}
{% if event.organizer %}
        <p class="event-meta">Organizer: {{ event.organizer }}</p>
{% endif %}
{% if event.description %}
        <p class="event-description">{{ event.description }}</p>
{% endif %}
{% if event.link and event.organizer != "SWERP" %}
        <p><a href="{{ event.link }}">Event link</a></p>
{% endif %}
      </article>
{% endif %}
{% endfor %}
{% if past_count == 0 %}
      <p class="events-empty">No past events are currently listed.</p>
{% endif %}
    </div>
  </section>
{% else %}
  <p class="events-empty">No events are currently listed.</p>
{% endif %}
</div>

<script src="https://cdn.jsdelivr.net/npm/fullcalendar@6.1.15/index.global.min.js"></script>
<script>
document.addEventListener("DOMContentLoaded", function () {
  var calendarElement = document.getElementById("events-calendar");

  if (!calendarElement || typeof FullCalendar === "undefined") {
    return;
  }

  var calendar = new FullCalendar.Calendar(calendarElement, {
    initialView: "dayGridMonth",
    height: "auto",
    timeZone: "Asia/Seoul",
    events: "{{ '/events.json' | relative_url }}",
    eventClick: function (info) {
      if (info.event.url) {
        info.jsEvent.preventDefault();
        window.open(info.event.url, "_blank", "noopener");
      }
    }
  });

  calendar.render();
});
</script>
