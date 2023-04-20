# weather
Weather information from the command line

### What's this?
This is a small Python script that allows you to get custom-formatted (similar to the ``date`` command) weather information from OpenWeatherMap directly from the command line.

It's intended for use with status bars such as [ironbar](https://github.com/JakeStanger/ironbar).

### Requirements
- Linux or similar UNIX based system
- Python3
- OpenWeatherMap API Key ([get yours here](https://home.openweathermap.org/api_keys))
- FontAwesome system font (optional for displaying weather icons)

### Installation
Clone the repository

```bash
git clone git@github.com:Xenorio/weather.git
cd weather
```

Install dependencies

```bash
pip3 install -r requirements.txt
```

Make it accessible from everywhere (optional)

```bash
sudo ln -s /path/to/repository/weather /usr/bin/
```

#### Icons
To be able to use the ``%I`` parameter to display weather icons, you need to either install FontAwesome as a system font, or edit the icons in source code to reflect a font of your choice.

Installing FontAwesome on Arch:
```bash
sudo pacman -S ttf-font-awesome
```

### Usage

#### First run
On the first execution, you need to supply your API key. This will be stored at ``~/.config/weather/keyfile`` and read from there on future executions. Supplying the key argument again overwrites this file. You can also edit it manually.

```bash
weather '%TC - %I %D' -q 'London' -k YOUR_KEY
```

#### Subsequent runs
```bash
weather '%T°C - %D' -q 'London'
```

In this example, the first argument is your format. the "%" values will be replaced with their corresponding information. See ``weather --help`` for a list of available variables.

``-q`` or ``--query`` is the search query for the desired location. Often, just a city name is enough. You can further specify using country codes, like ``London,GB``.

Example output:
```
10°C - clear sky
```

#### Watch mode
In watch mode, the script will keep running until it is killed, and output a new line of weather information using the supplied interval in seconds.

This will update every hour:

```bash
weather '%T°C - %D' -q 'London' --watch 3600
```

#### In status bars
For use in a status bar, first do a manual run to save your key. Then, add a command widget to your bar which executes weather. Make sure to set an interval so you don't hit API rate limits (1h is recommended, weather doesn't change that often).

Example status bar configurations can be found in the ``examples`` directory. If you make your own for a bar that has no example, a pull request would be much appreciated!

### Contributing
Please, don't be afraid of making PRs! 