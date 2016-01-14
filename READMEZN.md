# rc-form-submitter-behavior

`rc-form-submitter-behavior` 可以帮助你实现一个检验表单的行为——通过触发submitForm()方法去检验表单，表单验证通过则执行validatedSubmit()方法，否则执行invalidatedSubmit()。

#### 表单的设置，其必须是一个[`iron-form`](https://elements.polymer-project.org/elements/iron-form)。
##### Example:
```html
<form is="iron-form" id=“myForm”>
  <paper-input label="用户名" pattern=".+"/>
  <paper-input label="密码" type="password" pattern=".+"/>
  <button on-tap="submitForm">提交</button>
</form>
```

#### 通过`form`这个属性拿到表单信息。

##### Example:
```js
properties: {
  form: {
    type: Object,
    value: function() {
      return this.$.myForm;
    }
  }
}
```

#### 如果表单通过了验证，我们可以在validatedSubmit()方法里边设置验证通过之后的逻辑：
（formData为一个Object，里边包含着表单的数据。）
##### Example:
```js
validatedSubmit: function(formData) {
  window.alert('恭喜，通过验证！');
}
```

#### 如果表单没有通过验证，我们可以在invalidatedSubmit()方法里边设置逻辑：
##### Example:
```js
invalidatedSubmit: function() {
  window.alert('对不起，没有通过验证！');
}
```