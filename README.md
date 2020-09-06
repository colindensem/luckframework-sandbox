# Sandbox

This is a project written using [Lucky](https://luckyframework.org). Enjoy!

Open in VS Code with remote containers extension installed to open in a docker container.

Run all commands from the integrated terminal.

### Setting up the project

1. [Install required dependencies](https://luckyframework.org/guides/getting-started/installing#install-required-dependencies)
1. Update database settings in `config/database.cr`
1. Run `script/setup`
1. Run `lucky dev` to start the app
1. Open `localhost:3001` to view the app

### Testing

1. Run `crystal spec`
1. If it fails on LuckyFlow, open up `configure_lucky_flow.cr` and add the path for the chromedirver e.g. `settings.chromedriver_path = "/usr/bin/chromedriver"`
1. Re-run step 1

### Learning Lucky

Lucky uses the [Crystal](https://crystal-lang.org) programming language. You can learn about Lucky from the [Lucky Guides](https://luckyframework.org/guides/getting-started/why-lucky).
