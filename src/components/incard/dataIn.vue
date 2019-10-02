<template>
  <div>
    <div class="card-content">
      <b-field label="เลขบัตรประจำตัวประชาชน :" :type="{ 'is-danger': hasError }"
            :message="{ 'ใส่ตัวเลข 0-9 เท่านั้น': hasError }">
        <b-input v-model="patientInfo.cardId"></b-input>
      </b-field>
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
      <b-field>
        <b-field label="วันเกิด">
          <b-datepicker
            placeholder="select a date..."
            icon="calendar-today"
            v-model="patientInfo.birthDay"
          ></b-datepicker>
        </b-field>
        <b-field label="ศาสนา">
            <b-select v-model="patientInfo.religion">
                <option 
                    v-for="item in religionAll"
                    :value="item.religionSelect"
                    :key="item.id">
                    {{ item.religionSelect }}
                </option>
            </b-select>
        </b-field>
      </b-field>
      <b-field>
        <b-field label="เชื้อชาติ">
            <b-select v-model="patientInfo.nationality">
                <option 
                    v-for="item in nationalityLabel"
                    :value="item.select"
                    :key="item.id">
                    {{ item.select }}
                </option>
            </b-select>
        </b-field>
        <b-field label="สัญชาติ">
            <b-select v-model="patientInfo.origin">
                <option 
                    v-for="item in originLabel"
                    :value="item.select"
                    :key="item.id">
                    {{ item.select }}
                </option>
            </b-select>
        </b-field>
      </b-field>
      <b-field>
        <b-field label="เพศ :">
          <b-radio v-model="patientInfo.gender"
                name="gender"
                native-value="ชาย">
                ชาย
          </b-radio>
          <b-radio v-model="patientInfo.gender"
                name="gender"
                native-value="หญิง">
                หญิง
          </b-radio>
        </b-field>
        <b-field label="อาชีพ">
          <b-select v-model="patientInfo.carrer">
                <option 
                    v-for="item in carrerLabel"
                    :value="item.select"
                    :key="item.id">
                    {{ item.select }}
                </option>
            </b-select>
        </b-field>
      </b-field>
      <b-field>
        <b-field label="สถานภาพ :">
          <b-radio v-model="patientInfo.status"
                name="name"
                native-value="โสด">
                โสด
          </b-radio>
          <b-radio v-model="patientInfo.status"
                name="name"
                native-value="แต่งงานแล้ว">
                แต่งงานแล้ว
          </b-radio>
        </b-field>
      </b-field>
      <b-field>
        <b-field label="อาการเบื้องต้น">
            <b-input maxlength="200" type="textarea" v-model="patientInfo.symtoms"></b-input>
        </b-field>
      </b-field>
      <b-field>
        <b-field label="บ้านเลขที่">
          <b-input v-model="patientInfo.houseNum"></b-input>
        </b-field>
        <b-field label="หมู่">
          <b-input v-model="patientInfo.moo"></b-input>
        </b-field>
      </b-field>
      <b-field>
        <b-field label="ตำบล">
          <b-select v-model="patientInfo.tambon">
                <option 
                    v-for="item in carrerLabel"
                    :value="item.select"
                    :key="item.id">
                    {{ item.select }}
                </option>
            </b-select>
        </b-field>
        <b-field label="อำเภอ">
          <b-select v-model="patientInfo.aumpue">
                <option 
                    v-for="item in carrerLabel"
                    :value="item.val"
                    :key="item.id">
                    {{ item.select }}
                </option>
            </b-select>
        </b-field>
        <b-field label="จังหวัด">
          <b-select v-model="patientInfo.province">
                <option 
                    v-for="item in provinceLabel"
                    :value="item.val"
                    :key="item.id">
                    {{ item.select }}
                </option>
            </b-select>
        </b-field>
      </b-field>
      <b-field>
        <b-field label="เบอร์โทรศัพท์">
          <b-input v-model="phone"></b-input>
        </b-field>
        <b-field label="e-mail">
          <b-input v-model="email"></b-input>
        </b-field>
      </b-field>
      <b-field>
        <b-field label="ชื่อบิดา">
          <b-input v-model="patientInfo.dadFirstName"></b-input>
        </b-field>
        <b-field label="นามสกุลบิดา">
          <b-input v-model="patientInfo.momLastName"></b-input>
        </b-field>
      </b-field>
      <b-field>
        <b-field label="ชื่อมารดา">
          <b-input v-model="patientInfo.momFirstName"></b-input>
        </b-field>
        <b-field label="นามสกุลมารดา">
          <b-input v-model="patientInfo.momLastName"></b-input>
        </b-field>
      </b-field>
    </div>
    <p>{{patientInfo}}</p>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      patientInfo: {
        cardId: "",
        callAs: "",
        firstName: "",
        lastName: "",
        birthDay: "",
        religion: "",
        nationality: '',
        origin: "",
        gender: "",
        status: "",
        carrer: "",
        symtoms: '',
        houseNum: '',
        moo: 0,
        tambon: "",
        aumpue: "",
        province: "",
        phone: "",
        email: "",
        dadFirstName: "",
        dadLastName: "",
        momFirstName: "",
        momLastName: "",
      },
      hasError: false,
      religionAll: [
        {id:"0",religionSelect:"พุธ"},
        {id:"1",religionSelect:"คริส"},
        {id:"2",religionSelect:"อิสลาม"}
      ],
      nationalityLabel: [
        {id:"0",select:"ไทย"},
        {id:"1",select:"อินเดีย"},
        {id:"2",select:"ปากีสถาน"},
        {id:"3",select:"จีน"},
      ],
      originLabel: [
        {id:"0",select:"ไทย"},
        {id:"1",select:"อินเดีย"},
        {id:"2",select:"ปากีสถาน"},
        {id:"3",select:"จีน"},
      ],
      carrerLabel: [
        {id:"0",select:"นักษึกษา"},
        {id:"1",select:"ข้าราชการ"},
        {id:"2",select:"ธุรกิจส่วนตัว"},
        {id:"3",select:"พนักงานบริษัท"},
      ],
      provinceLabel: [
        {id:"0",select:"กรุงเทพ",val:"aumpueOfBkk"},
        {id:"1",select:"มุกดาหาร",val:"aumpueOfMuk"},
      ],
      aumpueOfBkk: [
        {id:"0",select:"อำเภอ1",val:"tambonOfAo"},
        {id:"1",select:"อำเภอ2",val:"tambonOfAt"},
      ],
      aumpueOfMuk: [
        {id:"0",select:"คำชะอี",val:"tambonOfKam"},
        {id:"1",select:"เมือง",val:"tambonOfMuk"},
      ],
      tambonOfAo: [
        {id:"0",select:"กทม11"},
        {id:"1",select:"กทม12"},
      ],
      tambonOfAt: [
        {id:"0",select:"กทม21"},
        {id:"1",select:"กทม22"},
      ],
      tambonOfKam: [
        {id:"0",select:"คำชะอี1"},
        {id:"1",select:"คำชะอี2"},
      ],
      tambonOfMuk: [
        {id:"0",select:"มุก1"},
        {id:"1",select:"มุก2"},
      ],
    };
  }
};
</script>