# Sending emails using smtpjs

{% embed url="https://smtpjs.com/" %}

```text
<script src="https://smtpjs.com/v3/smtp.js">
</script>
```

```text
Email.send({
    Host : "smtp.yourisp.com",
    Username : "username",
    Password : "password",
    To : 'them@website.com',
    From : "you@isp.com",
    Subject : "This is the subject",
    Body : "And this is the body"
}).then(
  message => alert(message)
);
```

