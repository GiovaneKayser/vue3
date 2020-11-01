<template>
  <div class="m-auto">
    <h1 class="text-2xl my-2 text-center">Vue Calendar</h1>
    <section class="mx-2 flex justify-between">
      <h2 class="font-bold">{{ currentMonthName }}</h2>
      <h2 class="font-bold">{{ currentYear }}</h2>
    </section>
    <section class="flex">
      <p
        class="text-center my-2"
        style="width: 14.28%"
        v-for="day in days"
        :key="day"
      >
        {{ day }}
      </p>
    </section>
    <section class="flex flex-wrap">
        <!-- p para inserir espaços em branco nos dias que não começam o mes -->
      <p
        class="text-center"
        style="width: 14.28%"
        v-for="num in startDay()"
        :key="num"
      ></p>
      <p
        class="text-center"
        style="width: 14.28%"
        v-for="num in daysInMonth()"
        :key="num"
        :class="currenDateClass(num)"
      >
        {{ num }}
      </p>
    </section>
    <section class="flex justify-between">
      <button class="px-2 border rounded" @click="prev">Prev</button>
      <button class="px-2 border rounded" @click="next">Next</button>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentDate: new Date().getUTCDate(),
      currentMonth: new Date().getMonth(),
      currentYear: new Date().getFullYear(),
      days: ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"],
    };
  },
  methods: { 
      //dias de um mes
    daysInMonth() {
      return new Date(this.currentYear, this.currentMonth + 1, 0).getDate();
    },
    //dia que começa o meu
    startDay() {
      return new Date(this.currentYear, this.currentMonth, 1).getDay();
    },
    //avance
    next() {
      if (this.currentMonth === 11) {
        this.currentMonth = 0;
        this.currentYear++;
      } else {
        this.currentMonth++;
      }
    },
    //recue o mes
    prev() {
      if (this.currentMonth === 0) {
        this.currentMonth = 11;
        this.currentYear--;
      } else {
        this.currentMonth--;
      }
    },
    //método para testar se o dia atual é do mesmo mes mostrado
    currenDateClass(num){
        const calenderFullDate = new Date(this.currentYear, this.currentMonth, num).toDateString()
        const currentFullDate = new Date().toDateString();
        return calenderFullDate === currentFullDate ? 'text-yellow-600' : '';
    }
  },
  computed:{
      currentMonthName(){
             return new Date(this.currentYear,this.currentMonth).toLocaleString("default", { month: "long" })

      }
  }
};
</script>

<style>
</style>