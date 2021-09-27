<template>
  <div class="overlay" 
  v-bind:class="{open:popupIsActive}"
  >
    <div class="popup">
      <div class="popup-content">
        <div class="popup-close">
          <button class="popup-close-btn" 
          v-on:click="popupHide">
            <svg xmlns="http://www.w3.org/2000/svg" width="10" height="10" viewBox="0 0 10 10" fill="none">
            <path fill-rule="evenodd" clip-rule="evenodd" d="M10 0.875L9.125 0L5 4.125L0.875 0L0 0.875L4.125 5L0 9.125L0.875 10L5 5.875L9.125 10L10 9.125L5.875 5L10 0.875Z" fill="black"/>
            </svg>
          </button>
          </div>
          <div class="popup-title">{{ title }}</div>
          <div class="popup-message">
             {{ message }} {{ email }}
          </div>
         <div class="popup-footer">
           <div class="actions">
             <a href="" class="action-button">{{ checkMail }}</a>

             <div class="help">
               <span class="question">{{ question }}</span>
                <a href="" class="action-link"> {{ checkMailElse }}</a>
              </div>
             </div>
             
           <div class="popup-picture"> </div>
         
        </div>
      </div>
      <!-- /.popup-content -->
    </div>
    <!-- /.popup -->
  </div>
  <!-- /.overlay --> 
</template>

<script>
export default {
  name: 'Popup',
  props: {
    message: String,
    email: String,
    title: String,
    checkMail: String,
    question: String,
    checkMailElse: String
  },
  data() {
    return {
      popupIsActive: false
    }
  },
   mounted() {
        //open popup after 10 sec
        setTimeout(() =>{
          this.popupShow()
        }, 10000)
      },
  methods: {
    //open popup and remove page scroll
    popupShow() {
      this.popupIsActive = true;
      const html = document.querySelector('html');
      html.classList.add('hidden');
    },
    //hide popup and return page scroll
    popupHide() {
      this.popupIsActive = false;
      const html = document.querySelector('html');
      html.classList.remove('hidden');
    }
  } 
}
</script>

<style scoped>

</style>