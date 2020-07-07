# Node-Mail-Helper

Nodemailer Helper For Sending Eamils With Ejs Templating

## Install

```
npm install node-mail-helper
```

## Prerequisite

This package requires the following evirmement configs

```
MAIL_DRIVER=smtp
MAIL_HOST=smtp.mailtrap.io
MAIL_PORT=2525
MAIL_USERNAME=xxxxxxxxxxx
MAIL_PASSWORD=xxxxxxxxxxx
MAIL_ENCRYPTION=
MAIL_FROM=no-reply@ndiecodes.com
```

N/B: MAIL_ENCRYPTION should be `tls` or `ssl` for secure channels and `blank` for unsecure channels.

## Usage

```
const Mail = require("node-mail-helper");
const path = require("path");

const templatePath = path.join(__dirname, "./email/welcome.ejs");

const mail = new Mail();
 await mail
      .to(user.email)
      .template(templatePath) //full path to your ejs file
      .subject("Welcome Email")
      .data(mailData)
      .send();
```

### The bellow example has all available methods

```
const Mail = require("node-mail-helper");
const path = require("path");

const templatePath = path.join(__dirname, "./email/welcome.ejs");

const attactments = [
        {   // utf-8 string as an attachment
            filename: 'text1.txt',
            content: 'hello world!'
        },
        {   // binary buffer as an attachment
            filename: 'text2.txt',
            content: new Buffer('hello world!','utf-8')
        },
];

const mail = new Mail();
 await mail
      .from("no-reply@ndiecodes.com")
      .to(user.email)
      .cc("janedoe@gmail.com")
      .bcc("johndoe@gmail.com")
      .text("String Represenation of Email Body")
      .template(templatePath)
      .subject("Welcome Email")
      .attachments(attachments)
      .data(mailData)
      .send();
```
## License

MIT