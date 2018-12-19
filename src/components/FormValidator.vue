<script>
export default {
  name: "FormValidator",
  props: ["watchHandler", "onBlur", "message"],
  data() {
    return {
      input: ""
    };
  },
  computed: {
    mssg() {
      if (this.message) {
        return this.message;
      }
      return "Bad input";
    }
  },
  watch: {
    input(newValue) {
      if (this.watchHandler) {
        const { isValid, value } = this.watchHandler(newValue);
        this.input = value;
        if (!isValid) {
          this.badInput();
        }
      }
    }
  },
  methods: {
    badInput() {
      this.$parent.$emit("badInput", this.mssg);
      this.$parent.$emit("input", this.input);
    },
    validInput() {
      this.$emit("validInput", this.mssg);
    },
    emitInput() {
      this.$emit("input", this.input);
    }
  },
  render() {
    return this.$scopedSlots.default({
      inputProps: { input: this.input },
      inputEvents: { input: evt => (this.input = evt.target.value) }
    });
  }
};
</script>
