<template>
  <div id="app">
    <h1>📅 Расписание на сегодня</h1>
    <div id="schedule">
      <div v-if="todaySchedule.length === 0">
        <p>🛌 Relax</p>
      </div>
      <div v-else>
        <div
          v-for="(item, index) in todaySchedule"
          :key="index"
          class="schedule-item"
        >
          <div class="time">🕒 {{ item.time }}</div>
          <div class="subject">📚{ { item.subject }}</div>
          <div class="location">🚪 {{ item.location }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      todaySchedule: [],
      schedules: {
        Monday: [
          {
            time: '16:10 - 17:00',
            subject: "Разработка UX/UI, 'ЛЗ' (МООК К.)",
            location: 'МООК',
          },
          {
            time: '17:20 - 18:10',
            subject: "Разработка UX/UI, 'ЛЗ' (МООК К.)",
            location: 'МООК',
          },
          {
            time: '18:30 - 19:20',
            subject: "Web-технологии, 'СПЗ' (МООК К.)",
            location: 'МООК',
          },
          {
            time: '19:30 - 20:20',
            subject:
              "Архитектура и организация компьютерных систем, 'СРСП' (Mohsin F.A.)",
            location: 'Online 10',
          },
          {
            time: '20:30 - 21:20',
            subject: "Культурология, 'Л' (Танабаева А.С.)",
            location: 'Online 12',
          },
        ],
        Tuesday: [
          {
            time: '10:00 - 10:50',
            subject:
              "Архитектура и организация компьютерных систем, 'Л' (Mohsin F.A.)",
            location: 'online 1',
          },
          {
            time: '18:30 - 19:20',
            subject: "Алгоритмы и структуры данных, 'ЛЗ' (МООК К.)",
            location: 'МООК',
          },
          {
            time: '19:30 - 20:20',
            subject: "Алгоритмы и структуры данных, 'ЛЗ' (МООК К.)",
            location: 'МООК',
          },
        ],
        Wednesday: [
          {
            time: '18:30 - 19:20',
            subject: 'Алгоритмы и структуры данных.',
            location: 'МООК',
          },
          {
            time: '19:30 - 20:30',
            subject: 'Алгоритмы и структуры данных.',
            location: 'МООК',
          },
          {
            time: '20:30 - 21:20',
            subject: "Психология 'СРСП', (Есенқожа Е.М.)",
            location: 'Online 11',
          },
        ],
        Thursday: [
          {
            time: '12:10 - 13:00',
            subject: "Java 'Practice'.",
            location: '703 Main',
          },
          {
            time: '13:10 - 14:00',
            subject: "Java 'Practice'.",
            location: '703 Main',
          },
          {
            time: '14:10 - 15:00',
            subject: "Java 'Lecture', Жакыпбеков C.Ж.",
            location: '700 Main',
          },
          {
            time: '15:10 - 16:00',
            subject: "Architecture of Computer System 'Маметова Р.И.",
            location: '604 Main',
          },
          {
            time: '16:10 - 17:00',
            subject: "Architecture of Computer System 'Маметова Р.И.",
            location: '604 Main',
          },
          {
            time: '17:20 - 18:10',
            subject: "Java 'Practice'.",
            location: '604 Main',
          },
          {
            time: '19:30 - 20:20',
            subject: 'Web technologies',
            location: 'МООК',
          },
        ],
        Friday: [
          {
            time: '09:00 - 09:50',
            subject: 'Psychology, Lecture (Есенқожа)',
            location: '303 - 4, Baizak center',
          },
          {
            time: '10:00 - 10:50',
            subject: 'Psychology, Practice (Есенқожа)',
            location: '708 main',
          },
          {
            time: '11:00 - 11:50',
            subject: 'Culturology, Practice (Танабаева А.С.)',
            location: '701',
          },
          {
            time: '17:20 - 18:10',
            subject: "Culturology, 'СРСП', (Танабаева А.С.)",
            location: 'Online 10',
          },
          {
            time: '18:30 - 20:20',
            subject: "Web - technologies, 'ЛЗ', (МООК К.)",
            location: 'МООК',
          },
        ],
        Saturday: [
          {
            time: '17:20 - 18:10',
            subject: "Web - technologies 'МООК'.",
            location: 'МООК',
          },
          {
            time: '18:30 - 20:20',
            subject: "UX/UI, 'СРСП'",
            location: 'МООК',
          },
          {
            time: '20:30 - 21:20',
            subject: "Java 'СРСП'. (Жакыпбеков С.Ж)",
            location: 'Online 13',
          },
        ],
      },
    };
  },
  created() {
    this.loadScheduleForToday();
  },
  methods: {
    loadScheduleForToday() {
      const weekdays = [
        'Sunday',
        'Monday',
        'Tuesday',
        'Wednesday',
        'Thursday',
        'Friday',
        'Saturday',
      ];
      const today = new Date();
      const weekday = weekdays[today.getDay()];

      if (weekday === 'Sunday') {
        this.todaySchedule = [];
      } else if (this.schedules[weekday]) {
        this.todaySchedule = this.schedules[weekday];
      } else {
        this.todaySchedule = [];
      }
    },
  },
};
</script>

<style>
body {
  font-family: Arial, sans-serif;
  padding: 20px;
}
.schedule-item {
  margin-bottom: 20px;
}
.time {
  font-weight: bold;
  font-size: 1.1em;
}
.emoji {
  font-size: 1.2em;
}
.subject {
  margin: 5px 0;
}
.location {
  color: gray;
}
</style>
