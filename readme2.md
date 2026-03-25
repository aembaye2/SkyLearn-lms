# SkyLearn Setup Fixes Summary

This update includes local development fixes and onboarding improvements.

## What Was Changed

- Added localhost support in Django hosts configuration.
- Added trusted CSRF origins for localhost over both HTTP and HTTPS.
- Pinned setuptools to `80.9.0` to avoid `pkg_resources` runtime errors with `django-model-utils==4.3.1`.
- Improved setup steps in the main README:
  - added explicit virtual environment creation/activation
  - added `.env` bootstrap command (`cp .env.example .env`)

## Why These Changes Were Needed

- `DisallowedHost` was raised for `localhost:8000` because localhost was missing from `ALLOWED_HOSTS`.
- CSRF origin checks failed for `https://localhost:8000`.
- Newer setuptools versions removed `pkg_resources`, which caused startup/migration failures in this dependency stack.

## Files Updated

- `config/settings.py`
- `requirements/base.txt`
- `README.md`

## Result

A fresh clone can install dependencies and run migrations/server locally with fewer setup errors.
