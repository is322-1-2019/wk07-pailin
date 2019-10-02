<template>
    <div class="card-content">
        <b-field label="ประวัติการแพ้ยา :">
            <b-radio
                v-model="allergic"
                name="name"
                value="false"
            >ไม่เคยแพ้</b-radio>
            <b-radio
                v-model="allergic"
                name="name"
                value="true"
            >เคยแพ้</b-radio>
        </b-field>
    </div>
</template>

<script>
export default {
    data: function() {
        return {
            allergic: false
        }
    }
}
</script>