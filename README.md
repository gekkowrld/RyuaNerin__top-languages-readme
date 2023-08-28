# Top-Langauges - Readme

![preview](README.png)

Add development language usage statistics on your Profile Readme.

Did not need to fork this repository.

## Usage

1. Go to your Profile Readme

1. move to `<username>/<username>/actions`

1. Click New workflow

1. Set up a workflow yourself

1. Delete the default content

1. copy the following code and paste it to your new workflow

   ```yml
   name: Top-Languages Readme

   on:
     workflow_dispatch:
     schedule:
       # Runs at 12am UTC
       - cron: "0 0 * * *"

   jobs:
     update-readme:
       name: Update this repo's README
       runs-on: ubuntu-latest
       steps:
         - uses: gekkowrld/langs-readme@gekkowrld
   ```

1. Add a comment to your README.md like this:

   ```md
   <!--START_SECTION:top_language-->
   <!--END_SECTION:top_language-->
   ```

1. Go to Action menu

1. Click `Top-Languages Readme` under `All workflows`

1. Click `Run workflow`

## Including private repository

1. Move to [**Github Settings -> Developer settings -> Personal access tokens** -> Generate new token](https://github.com/settings/tokens/new)

1. Check **repo**

1. Click `generate token`

1. Copy `token`

   ![token generated](README-1.png)

1. Go to your Profile Readme

1. Move to `Settings` -> `Secrets`

1. Click `New Secret`

1. input `GH_TOKEN` in **Name**

1. input the copied token in **Value**

1. Click `Add secret`

1. Edit you workflow file

   ```yml
   name: Top-Languages Readme

   on:
     workflow_dispatch:
     schedule:
       # Runs at 12am UTC
       - cron: "0 0 * * *"

   jobs:
     update-readme:
       name: Update this repo's README
       runs-on: ubuntu-latest
       steps:
         - uses: gekkowrld/langs-readme@gekkowrld
           with:
             GH_TOKEN: ${{ secrets.GH_TOKEN }}
   ```

## With option (Optional)

```yml
name: Top-Languages Readme

on:
  workflow_dispatch:
  schedule:
    # Runs at 12am UTC
    - cron: "0 0 * * *"

jobs:
  update-readme:
    name: Update this repo's README
    runs-on: ubuntu-latest
    steps:
      - uses: gekkowrld/langs-readme@gekkowrld
        with:
          COMMIT_MESSAGE: "" #Optional
          USERNAME: <username> # Optional
          LINE_FORMAT: "$NAME   $SIZE $BAR  $PERCENT" # Optional
          LIST_COUNT: 10 # Optional
          BLOCKS: "░█" # Optional
          BAR_WIDTH: 25 # Optional
          SHOW_TOTAL: false # Optional
          TOP_TOTAL: false # Optional
          SHOW_TOTAL_SEPARATOR: true # Optional
```

The default commit message is:
```txt
      docs(readme): Update README with ``username``'s current language usage

      Update the README file to include current statistics generated on ``full_year`` at ``full_time`` UTC.

      Committed by <github-actions[bot]> on behalf of <``username``>.
```

The COMMIT_MESSAGE can be "personalized" by using the following variables:

| Variable | Description |
|---|---|
|date| Sets the current date (%Y %H:%M%S)|
|year| Sets the current year|
|month_name| Sets the current month name|
|month_no| Sets the current month number (0 index)|
|day_name| Sets the current day name|
|day_no| Sets the current day number(0 index)|
|hour| Sets the current hour|
|minute| Sets the current minute|
|username| Sets the github username|


- BLOCKS styles:

  - default : `░█`

  | BLOCKS     | default | example (55.5%) |
  | ---------- | :-----: | --------------- |
  | ` █`       |    O    | `██████    `    |
  | `░█`       |         | `██████░░░░`    |
  | `░▒▓█`     |         | `█████▓░░░░`    |
  | `⣀⣄⣤⣦⣶⣷⣿`  |         | `⣿⣿⣿⣿⣿⣶⣀⣀⣀⣀`    |
  | `⣀⣄⣆⣇⣧⣷⣿`  |         | `⣿⣿⣿⣿⣿⣧⣀⣀⣀⣀`    |
  | `▁▂▃▄▅▆▇█` |         | `█████▅▁▁▁▁`    |
  | `▏▎▍▌▋▊▉█` |         | `█████▋▏▏▏▏`    |
  | `○◔◐◕⬤`    |         | `⬤⬤⬤⬤⬤◕○○○○`    |
  | `□◱◧▣■`    |         | `■■■■■▣□□□□`    |
  | `□◱▨▩■`    |         | `■■■■■▩□□□□`    |
  | `□▨▩■`     |         | `■■■■■▩□□□□`    |
  | `□◱▥▦■`    |         | `■■■■■▦□□□□`    |
