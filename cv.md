1. **Name Surname:** Mikhail ELUFERIEV
2. **Contacts:**
    * _e-mail:_ yourstryly.bill@gmail.com
    * _telegramm:_ @YT_YT
3. **About me:**
I work as engineer at Smartec. Now I'm working as frontend under web-application 'HR platform' for internal utilisation at our company. I want to improve my programming skills and I want to find new job in IT.
4. **Skills:**
    * _programming skills:_
        * JS
        * Java
        * Python
        * VB
    * _frameworks:_
        * VueJS
        * Android Studio
5. **Code examples:**
InputDatePicker.vue - reusable component for input type "Date" in russian localization (date format RU: 'DD.MM.YYYY')
```
<template>
    <b-input-group
    style="width: 100%;">
        <b-form-input
        class="inp-form-personal-data"
        v-model="stringDate"
        type="text"
        :state="validation"
        :readonly="isDisabled"
        @change="OnDateChange"
        ></b-form-input>
        <b-input-group-append>
            <b-form-datepicker
            v-model="dateDate"
            button-only
            right
            locale="RU"
            :disabled="isDisabled"
            aria-controls="example-input"
            @context="OnContext"
            ></b-form-datepicker>
        </b-input-group-append>
        <b-form-invalid-feedback v-if="validationText !== ''" :state="validation">{{validationText}}</b-form-invalid-feedback>
        <b-form-valid-feedback v-if="validationText !== ''" :state="validation"></b-form-valid-feedback>
    </b-input-group>   
</template>

<script>
export default {
    name: 'InputDatePicker',
    props: {
        validationText: String,
        validation: true,
        isDisabled: Boolean,
        isTable: Boolean,
        updDate: String,
        objectName: String,
    },
    data() {
        return {
            stringDate: '',
        }
    },
    computed: {
        dateDate: {
            get: function() {
                return this.updDate;
            },
            set: function(value) {
                if (this.isTable) {
                     this.$emit('update-value', {date: value, name: this.objectName} );
                     this.$emit('update-date', {date: value, name: this.objectName} );
                } else {
                    this.$emit('update-date', {date: value, name: this.objectName} );
                }
            }
        }
    },
    methods: {
        OnDateChange(){
            let newArr = new Array();
            newArr = this.stringDate.split('.');
            if (newArr.length < 2) {
                this.$bvToast.toast(`Неверный формат даты, задайте формат в виде ДД.ММ.ГГГГ`, {
                    title: 'Ошибка',
                    autoHideDelay: 5000,
                    appendToast: true,
                })
                this.$emit('update-date', {date: undefined, name: this.objectName} );
            } else {
                let sDate = this.stringDate.split('.')[2] + '-' + this.stringDate.split('.')[1] + '-' + this.stringDate.split('.')[0];
                let dDate = new Date(sDate);
                if (dDate == 'Invalid Date') {
                    this.$bvToast.toast(`Неверный формат даты, задайте формат в виде ДД.ММ.ГГГГ`, {
                        title: 'Ошибка',
                        autoHideDelay: 5000,
                        appendToast: true,
                    })
                    this.$emit('update-date', {date: undefined, name: this.objectName} );
                } else {
                    if (this.isTable) {
                        this.$emit('update-value', {date: sDate, name: this.objectName} );
                        this.$emit('update-date', {date: sDate, name: this.objectName} );
                    } else {
                        this.$emit('update-date', {date: sDate, name: this.objectName} );
                    }
                }
            }
        },
        OnContext(value){
            let sDate = value.selectedYMD;
            let dDate = new Date(sDate);
            if (dDate == 'Invalid Date') {
                this.stringDate = '';
            } else {
                this.stringDate = dDate.toLocaleString('RU').split(',')[0];
            }
        },
    },
}
</script>

```
6. **Experience:** Lead engineer, Smartec, 2010 - until now
7. **Education:** 
  * _univercity:_ Samara State Aerospace Univercity 
  * _faculty:_ spacecrafts
  * _issue:_ 2009
8. **Languages:**
  * _French:_ B1 (Intermediate)
  * _English:_ A2 (Pre-Intermediate)