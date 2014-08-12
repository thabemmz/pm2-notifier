#pm2-newrelic-notifier
Send PM2 error notifications to newrelic. Both errors and notifications are configurable.

## To get it setup:
1. Generate `config.json`
2. Add your newrelic configuration in `newrelic.js`
3. Run it

### Generate `config.json`
Generate a `config.json` file in the main project directory, containing the PM2 events and the error message that's being sent to NewRelic.

Example:
```
"events": {
  "process:exit:overlimit": "[PM2] Exit Overlimit",
  "process:exception": "[PM2] Exception received"
}
```

A list of PM2 events:
- `process:online` when a process is started / restarted
- `process:exit` when a process is exited
- `process:exit:overlimit` when a process was restarted and exited the maximum allowed amount of times (15 by default)
- `process:exception` when a process has received an UncaughtException

A full list of PM2 events can be found at the (PM2 interface repository page)[https://github.com/Unitech/pm2-interface#notifications].

### Add your NewRelic configuration in `newrelic.js`
In order for NewRelic to work, it needs a configuration which requires at least an app_name and a license_key. Additional configuration options can be given here as well. NewRelic requires you to add this configuration in a `newrelic.js` file that has to exist in your main directory.

Full documentation of the NewRelic can be found at the (NodeJS NewRelic repository page)[https://github.com/newrelic/node-newrelic].

### Run it
Run your app
