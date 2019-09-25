<template>
  <div class="container">
      <section>
    <b-field label="เลขบัตรประจำตัวประชาชน :">
      <b-input type="number" v-model="patientInfo.cardId"></b-input>
    </b-field>
    <b-field>
      <b-field>
        <b-field label="คำนำหน้า">
          <b-select placeholder="คำนำหน้า" v-model="patientInfo.callAs">
            <option value="นาย">นาย</option>
            <option value="นาง">นาง</option>
            <option value="นางสาว">นางสาว</option>
            <option value="เด็กชาย">เด็กชาย</option>
            <option value="เด็กหญิง">เด็กหญิง</option>
          </b-select>
        </b-field>
        <b-field label="ชื่อ">
          <b-input v-model="patientInfo.firstName"></b-input>
        </b-field>
        <b-field label="นามสกุล">
          <b-input v-model="patientInfo.lastName"></b-input>
        </b-field>
      </b-field>
    </b-field>
    <b-field label="วันเกิด">
        <b-datepicker
            placeholder="select a date..."
            icon="calendar-today"
            v-model="patientInfo.birthDay">
        </b-datepicker>
    </b-field>
      </section>
      <p>{{patientInfo}}</p>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      patientInfo:{
        cardId: "",
        callAs: "",
        firstName: "",
        lastName: '',
        birthDay: ''
      }
    };
  }
};
</script>