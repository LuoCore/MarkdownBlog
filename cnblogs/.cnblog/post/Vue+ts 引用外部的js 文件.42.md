<div class="cnblogs_Highlighter">
<pre class="brush:javascript;gutter:true;">export default defineComponent({
  name: 'App',
  components: {
    Signin,
    Navbar,
    FooterPage,
    BackToTopButton,
    ToolbarForHandheldDevices
  },
  data() {
    return {
      activeClassValue: ""
    }
  },
  methods: {
    receiveActiove(res: string) {
      this.activeClassValue = res;
    }
  },
  mounted() {
    const bootstrapBundle = document.createElement('script');
    bootstrapBundle.type = 'text/javascript';
    bootstrapBundle.src = '../src/assets/vendor/bootstrap/dist/js/bootstrap.bundle.min.js';
    document.body.appendChild(bootstrapBundle);
    const simplebar = document.createElement('script');
    simplebar.type = 'text/javascript';
    simplebar.src = '../src/assets/vendor/simplebar/dist/simplebar.min.js';
    document.body.appendChild(simplebar);
    const tinySlider = document.createElement('script');
    tinySlider.type = 'text/javascript';
    tinySlider.src = '../src/assets/vendor/tiny-slider/dist/min/tiny-slider.js';
    document.body.appendChild(tinySlider);
    const smoothScrollPolyfills = document.createElement('script');
    smoothScrollPolyfills.type = 'text/javascript';
    smoothScrollPolyfills.src = '../src/assets/vendor/smooth-scroll/dist/smooth-scroll.polyfills.min.js';
    document.body.appendChild(smoothScrollPolyfills);
    const theme = document.createElement('script');
    theme.type = 'text/javascript';
    theme.src = '../src/assets/js/theme.min.js';
    document.body.appendChild(theme);
    
  }
});
</pre>
</div>
<p>&nbsp;这么麻烦的vue ？</p>
<p><span style="background-color: #ff0000;"><strong><span style="font-family: 黑体; font-size: 18px;">太瓜皮了，谁还有更好的办法，可以留言告诉我，我帮你们测试</span></strong></span></p>