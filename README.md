# gdrive-backup-cron

```javascript
const BackupService = require("gdrive-backup-cron");

let service = new BackupService({
  drive: {
    auth: {
      /* google service account configuration here*/
    },
    folder: "google drive shared folder id here",
    keep: 1,
  },
  sourceFolder: "source folder here",
  auto: {
    cron: "00 00 00 * * *",
    timezone: "Turkey",
  },
});

service.on("backup", (name, id) => {});
service.on("restore", (name, id) => {});

// local disk
service.backup({ saveTo: "./test.zip" }).then(() => {
  service.restore({ backupPath: "./test.zip" }).then(() => {});
});

// google drive
service.backup({ backupName: "test.zip" }).then(() => {
  service.restore({ backupName: "test.zip" }).then(() => {});
});
```
