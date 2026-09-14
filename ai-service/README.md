# AI Service

This folder will hold the AI service for FitFlow, kept separate from the main backend since it has different scaling and tooling needs.

## Planned Setup

- Python with FastAPI
- TensorFlow Lite for on-device style personalization
- Cloud based ML tools for the heavier models
- Computer vision for reading food photos

## What This Service Handles

- Generating personalized workout plans based on user history
- Recognizing food from photos for nutrition logging

The reasoning for keeping this as its own service instead of building it into the main backend is in [docs/adr.md](../docs/adr.md).


