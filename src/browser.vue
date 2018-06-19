<template>
    <div class="browser">
        Current Browser is {{ browser }}
    </div>
</template>

<script>
import Vue from 'vue'
export default {
    computed: {
        browser() {
            if((!!window.opr && !!opr.addons) || !!window.opera || navigator.userAgent.indexOf(' OPR/') >= 0) {
                return "Opera";
            } else if(typeof InstallTrigger !== 'undefined') {
                return "Firefox";
            } else if(/constructor/i.test(window.HTMLElement) || (function (p) { return p.toString() === "[object SafariRemoteNotification]"; })(!window['safari'] || safari.pushNotification)) {
                return "Safari";
            } else if(/*@cc_on!@*/false || !!document.documentMode) {
                return "Internet Explorer";
            } else if(!!window.chrome && !!window.chrome.webstore) {
                return "Chrome";
            } else if(!isIE && !!window.StyleMedia) {
                return "Edge";
            } else {
                return "Undefined";
            }
        }
    }
}
</script>

<style>
    .browser {
        font-family: tahoma;
        font-weight: bold;
    }
</style>