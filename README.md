# Purpose

As part of a larger system demo, this subsystem is going to be a React UI that calls a separate API.

## Tech Used

- .NET 7
- OpenApi

(not a TDD project)

# Status

Currently, a bare-bones skeleton for the eventual goal.  Runs in debug only for now, via the UI's launch settings environment variable for the API url.

# Details

## OpenAPI

Note that the swagger.json is currently manually copied when running the API in debug to the file in the UI project. 

There are [ways](https://techcommunity.microsoft.com/t5/healthcare-and-life-sciences/auto-regenerating-api-client-for-your-open-api-project/ba-p/3302390) to automate this.

# The System

Eventually, the overall system will consist of
1. This API, providing information from database (instead of the current mocked data from json configuration file)
    1. Will include stand-alone repo, ci-cd, testing up to the level of the api as a whole, and a docker container running the API
    1. This will include ci-cd all the way through deployment
1. A front-end UI interactively charting the data from the API, probably in Razor
    1. Will include stand-along repo, ci-cd, testing up to the level of the subystem (maybe using Playwright?), and a docker container running the UI
    1. This will include ci-cd all the way through deployment
1. An integration project solution that will orchestrate the api and UI in docker containers, with the ability to run ecosystem tests

- Each subsystem's project solution will have the ability to be run locally with or without its docker container, from the IDE or the command-line
- The integration project solution will be blocked from production

I chose to separate the api from the ui, instead of the usual minimal API approach of putting everything into the web front-end app -- sse *Separation of Concerns*


# Design

<mark>The design covers not only the actual apps -- the ui and api -- **BUT ALSO** the structure of the **repo**sitory, the **building**, the **testing**, the **publishing**, the **monitoring**.</mark>

The UI currently is a dumbed-down, write-text-directly to the browser.  It knows about the API it queries via OpenApi (swagger.json).

In the future, the UI will be ramped for a front-end UI framework -- probably React

## REPO

## TESTING

### CI-CD

TBD

### DEPLOYMENT

Currently, I've been running these only in debug, locally.  I do have a free Azure account that I may be able to deploy to.

### MONITORING

Explore Azure possibilities?

