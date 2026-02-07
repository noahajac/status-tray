# Changelog

All notable changes to Status Tray will be documented in this file.

Format based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

### Fixed
- Fixed icon tint effect not applying on GNOME 48+ (Mutter 18). The `ColorizeEffect.tint` property now expects a `Cogl.Color` instead of `Clutter.Color`. The extension now detects the available API at runtime, using `Cogl.Color.init_from_4f()` on GNOME 48+ and falling back to `Clutter.Color.new()` on GNOME 45-47.

## [1.0] - 2026-01-25

### Added
- Initial release completed
