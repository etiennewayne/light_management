<template>
    <div>
        <div class="section">
            <div class="columns is-centered">
                <div class="column is-6">
                    <div class="box">
                        <h1 class="title is-5">LAST REQUESTED APPOINTMENT</h1>
                        <div class="appointment-detail">
                            <div>
                                <strong>DATE:</strong> {{ appointment.app_date }}
                            </div>
                            <div>
                                <strong>TIME:</strong> {{ appointment.app_time }}
                            </div>
                            <div>
                                <strong>TRANING CENTER:</strong> {{ appointment.training_center }}
                            </div>
                            <div>
                                <strong>STATUS:</strong>
                                <span v-if="appointment.app_status == 1">APPROVED</span>
                                <span v-else-if="appointment.app_status == 2">CANCELLED</span>
                                <span v-else>PENDING</span>
                            </div>

                        </div>
                    </div>
                </div>
            </div>
        </div>

    </div>
</template>
<script>
export default {
    data(){
        return{
            appointment: {},
        }
    },

    methods: {
        getUpcommingAppointment(){
            axios.get('/my-upcoming-appointment').then(res=>{
                this.appointment = res.data;
            })
        }
    },
    mounted() {
        this.getUpcommingAppointment();
    }
}
</script>
<style scoped>
    .appointment-detail{

    }
</style>
