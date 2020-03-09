<template>
  <a-form :form="form" @submit="handleSubmit">
    <a-form-item v-bind="formItemLayout" label="姓名">
      <a-input
        v-decorator="[
          'password',
          {
            rules: [
              {
                validator: validateToNextPassword,
              },
            ],
          },
        ]"
        type="text"
      />
    </a-form-item>
    <a-form-item v-bind="formItemLayout" label="手机号码">
      <a-input
        v-decorator="[
          'phone',
          {
            rules: [{ required: true, message: '请输入正确的手机号码' }],
          },
        ]"
        style="width: 100%"
      >
        <a-select
          slot="addonBefore"
          v-decorator="['prefix', { initialValue: '86' }]"
          style="width: 70px"
        >
          <a-select-option value="86">+86</a-select-option>
          <a-select-option value="87">+87</a-select-option>
        </a-select>
      </a-input>
    </a-form-item>
     <a-form-item label="保险类型" v-bind="formItemLayout">
      <a-select
        v-decorator="[
          'select',
          { rules: [{ required: true, message: '请选择保险类型' }] },
        ]"
        placeholder="请选择保险类型"
      >
        <a-select-option value="china">
          寿险
        </a-select-option>
        <a-select-option value="usa">
          理财险
        </a-select-option>
        <a-select-option value="usb">
          车险
        </a-select-option>
      </a-select>
    </a-form-item>
    <a-form-item v-bind="formItemLayout" label="保险公司">
      <a-cascader
        v-decorator="[
          'residence',
          {
            initialValue: ['中国人寿', '上海分部', '金桥营业部'],
            rules: [
              { type: 'array', required: true, message: 'Please select your habitual residence!' },
            ],
          },
        ]"
        :options="residences"
      />
    </a-form-item>
      <a-form-item v-bind="formItemLayout" label="已购买保险全称">
      <a-input
        v-decorator="[
          'text',
          {
            rules: [
              {
                type: 'text',
                message: '请输入已购买保险名称',
              },
              {
                required: true,
                message: '请输入已购买保险名称',
              },
            ],
          },
        ]"
      />
    </a-form-item>

    <a-form-item v-bind="tailFormItemLayout">
      <!-- <a-checkbox v-decorator="['agreement', { valuePropName: 'checked' }]">
        I have read the
        <a href>agreement</a>
      </a-checkbox> -->
    </a-form-item>
    <a-form-item v-bind="tailFormItemLayout">
      <a-button type="primary" html-type="submit">立即评估</a-button>
    </a-form-item>
  </a-form>
</template>

<script>
const residences = [
  {
    value: "中国人寿",
    label: "中国人寿",
    children: [
      {
        value: "上海分部",
        label: "上海分部",
        children: [
          {
            value: "金桥营业部",
            label: "金桥营业部"
          }
        ]
      }
    ]
  },
  {
    value: "平安保险",
    label: "平安保险",
    children: [
      {
        value: "上海分部",
        label: "上海分部",
        children: [
          {
            value: "金桥营业部",
            label: "金桥营业部"
          },
          {
            value: "莘庄营业部",
            label: "莘庄营业部"
          },

        ]
      }
    ]
  }
];

export default {
  data() {
    return {
      confirmDirty: false,
      residences,
      autoCompleteResult: [],
      formItemLayout: {
        labelCol: {
          xs: { span: 24 },
          sm: { span: 8 }
        },
        wrapperCol: {
          xs: { span: 24 },
          sm: { span: 16 }
        }
      },
      tailFormItemLayout: {
        wrapperCol: {
          xs: {
            span: 24,
            offset: 0
          },
          sm: {
            span: 16,
            offset: 8
          }
        }
      }
    };
  },
  beforeCreate() {
    this.form = this.$form.createForm(this, { name: "register" });
  },
  methods: {
    handleSubmit(e) {
      e.preventDefault();
      this.form.validateFieldsAndScroll((err, values) => {
        if (!err) {
          console.log("Received values of form: ", values);
        }
      });
    },
    handleConfirmBlur(e) {
      const value = e.target.value;
      this.confirmDirty = this.confirmDirty || !!value;
    },
    compareToFirstPassword(rule, value, callback) {
      const form = this.form;
      if (value && value !== form.getFieldValue("password")) {
        callback("Two passwords that you enter is inconsistent!");
      } else {
        callback();
      }
    },
    validateToNextPassword(rule, value, callback) {
      const form = this.form;
      if (value && this.confirmDirty) {
        form.validateFields(["confirm"], { force: true });
      }
      callback();
    },
    handleWebsiteChange(value) {
      let autoCompleteResult;
      if (!value) {
        autoCompleteResult = [];
      } else {
        autoCompleteResult = [".com", ".org", ".net"].map(
          domain => `${value}${domain}`
        );
      }
      this.autoCompleteResult = autoCompleteResult;
    }
  }
};
</script>