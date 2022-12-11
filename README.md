# internationalization-automation

First of all, you have to add .credential in the translation folder.

.credential file is made of JSON file from google spreadsheet. 

To Make JSON file from google spreadsheet, you have to follow below process.

1. Go to [cloud platform](https://console.cloud.google.com/apis/dashboard?pli=1&project=vivid-router-350308, "cloud platform link")

2. Create API in Credentials tab

3. Create user credential (service account)

4. Modify that account service account (key)

5. Add key - Create a new key

6. Create JSON format

7. Save that file (needed by the project)

8. Set up sharing for that account email google spreadsheet

After then, you should create the translation/.credentials folder, save the JSON file downloaded from Google Spreadsheet. (note: Add that JSON file to git ignore)

Next, after creating the i18next-scanner.config.js file in the root, modify the configuration file.

Finally, you should add translation folder in your project, and add script to package.json like this.

```js
{
  "scan:i18n": "i18next-scanner --config i18next-scanner.config.js",
  "upload:i18n": "npm run scan:i18n && node src/translation/upload.js",
  "download:i18n": "node src/translation/download.js",
  "serve": "npm run download:i18n && vue-cli-service serve"
}
```

If your google-spreadsheet changes frequently, you could add download:18n in build time. 

