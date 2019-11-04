# ticker.fish

> Real-time stock tickers from the command-line.

`ticker.fish` is a [fish shell](https://fishshell.com/) function using the Yahoo Finance API as a data source. It features colored output and is able to display pre- and post-market prices.

![ticker.fish](https://raw.githubusercontent.com/parambirs/ticker.fish/master/screenshot.png)

## Install

```sh
~> curl -o $HOME/.config/fish/functions/ticker.fish https://raw.githubusercontent.com/parambirs/ticker.fish/master/ticker.fish
```

Make sure to install [jq](https://stedolan.github.io/jq/), a versatile command-line JSON processor.

## Usage

```fish
# Single symbol:
~> ticker AAPL

# Multiple symbols:
~> ticker AAPL MSFT GOOG BTC-USD

# Read from file:
~> echo "AAPL MSFT GOOG BTC-USD" > ~/.ticker.conf
~> ticker (string split " " <  ~/.ticker.conf)

# Use different colors:
~> set -x COLOR_BOLD "\e[38;5;248m"; \
  set -x COLOR_GREEN "\e[38;5;202m"; \
  set -x COLOR_RED "\e[38;5;154m"; \
  ticker AAPL

# Disable colors:
~> set -x NO_COLOR 1; ticker AAPL

# Update every five seconds:
~> while true; clear; ticker AAPL MSFT AMZN BTC-USD; sleep 5; end
```
