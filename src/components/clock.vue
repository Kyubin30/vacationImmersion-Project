<template>
  <div id="clock" class="none"> 
      <h1 class="none">{{whatTime}}</h1>
      <h2 class="none">{{whatDay}}</h2>
  </div>
</template>

<script>
export default {
    data(){
        return{
            whatTime: "00:00",
            whatDay: "Sun. January 1 2021"
        };
    },
    created(){
        const today = new Date();
        const monthList = new Array("January","February","March","April","May","June","July","August","september","October","November","December");
        const month = monthList[today.getMonth()];
        const date = today.getDate();
        const year = today.getFullYear();
        const weekList = new Array("Sun.", "Mon.", "Tue.", "Wed.", "Thu.", "Fri.", "Sat.");
        const week = weekList[today.getDay()];
        this.whatDay = `${week} ${month} ${date} ${year}`;
    },
    methods: {
        time(){
            setInterval(() => {
            const now = new Date();
            this.whatTime = `${this.checkSingleDigit(now.getHours())}:${this.checkSingleDigit(now.getMinutes())}`;
            },1000);
        },
        checkSingleDigit (digit) {
            return ('0' + digit).slice(-2)
        }
    },
    mounted(){
        this.time()
    }
}
</script>