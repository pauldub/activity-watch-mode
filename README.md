# Emacs Minor Mode for ActivityWatch

[![MELPA](https://melpa.org/packages/activity-watch-mode-badge.svg)](https://melpa.org/#/activity-watch-mode)

`activity-watch-mode` is an automatic time tracking extension for Emacs using [ActivityWatch](https://activitywatch.net/).

## Installation

Heads Up! ActivityWatch depends on [request.el](https://tkf.github.io/emacs-request/) being installed to work correctly.

It optionally depends on [Projectile](https://github.com/bbatsov/projectile) and [Magit](https://magit.vc) to detect project names.

1. Install activity-watch-mode for Emacs using [MELPA](https://melpa.org/#/activity-watch-mode).

3. Add `(global-activity-watch-mode)` to your `init.el` file, then restart Emacs.

6. Use Emacs with activity-watch-mode turned on and your time will be tracked for you automatically.

7. Visit http://localhost:5600 to see your logged time.

## Usage

Enable ActivityWatch for the current buffer by invoking `M-x activity-watch-mode`.  If you wish to activate it globally, run `M-x global-activity-watch-mode`.


## Configuration

Set variable `activity-watch-api-host` to your activity watch local instance (default to `http://localhost:5600`).

### Project Name Detection

By default, the extension will try to infer the name of the project by consulting Projectile and Magit. Users can add resolution methods by defining functions in the form `activity-watch-project-name-<NAME>` and then adding `'NAME` to the list of resolvers `activity-watch-project-name-resolvers`. See its documentation for a list of predefined resolvers.

The default project name used when a proper one cannot be determined is "unknown" and can be customized via `activity-watch-project-name-default`.

### Org-mode Integration (Optional)

You can automatically link your tracked time to specific Org-mode tasks. When an Org clock is active, the watcher can inject a specific property from the clocked task into the ActivityWatch payload.

To enable this feature, add the following to your configuration:

```elisp
(setq activity-watch-org-clock-active t)
(setq activity-watch-org-clock-property "TICKET_ID") ; Replace with your preferred property
```

Or if you use `use-package`:

```elisp
(use-package activity-watch-mode
  :ensure t
  :custom
  (activity-watch-org-clock-active t)
  (activity-watch-org-clock-property "TICKET_ID")
  :config
  (global-activity-watch-mode))
```

This is particularly useful for correlating time spent across different buffers (like *gptel*, *magit*, or source files) with a specific ticket or task ID defined in your Org files.


## Acknowledgments

This mode is based of the [wakatime-mode](https://github.com/wakatime/wakatime-mode).
