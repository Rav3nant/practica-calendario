<script setup lang="ts">
import { ref, onMounted, type Ref } from "vue";
import {
  type Configs,
  type Appointment,
  E_CustomEvents,
} from "./stores/events";

const evts: Ref<Appointment[]> = ref([
  {
    date: "2023-11-19T10:00:50.253Z",
    comment: "Peda deL Dia de la Revolución Mexicana",
    id: "cl3eddmjz1435801pqwfa5ihd1",
    keywords: "Peda",
    name: "Compas",
  },
  {
    date: "2023-11-21T14:00:00.000Z",
    comment: "Compras para cena navideña (congelados)",
    id: "cl32rbkjk1700101o53e3e3uhn",
    keywords: "Compras Navideñas",
    name: "Mamá",
  },
  {
    date: "2023-12-14T13:00:36.284Z",
    comment: "Inicio Oficial Vacaciones Invierno",
    id: "cl34856g01439801piot8vp3jr",
    keywords: "Vacaciones",
    name: "UNISON",
  },
  {
    date: "2022-11-28T07:00:00.000Z",
    comment: "Cita con el medico",
    id: "cl2yk477s136301pbmh49btdg",
    keywords: "Cita Medico",
    name: "Medico",
  },
  {
    date: "2022-11-08T07:00:00.000Z",
    comment: "Placeholder Evento",
    id: "cl30h76qi116501nu2dc1wnv1",
    keywords: "Placeholder",
    name: "Prueba",
  },
]);

const cfg = ref<Configs>({
  viewEvent: undefined,
  reportEvent: {
    icon: true,
    text: "",
  },
  searchPlaceholder: "",
  eventName: "",
  closeText: "",
  nativeDatepicker: true,
  todayButton: true,
  firstDayOfWeek: 1,
});

onMounted(() => {
  [E_CustomEvents.VIEW, E_CustomEvents.REPORT].forEach((e: string) => {
    document.body.addEventListener(e, (event: Event | CustomEvent) => {
      console.log({ event });
    });
  });
});
</script>

<template>
  <pro-calendar
    date="2022-11-10T00:00:00.000Z"
    :events="evts"
    :config="cfg"
    @calendarClosed="void 0"
    @fetchEvents="void 0"
    :loading="false"
  />
</template>

<style scoped></style>
