Humans & Heroes
===============
[Front page](https://skyspiral7.github.io/Humans-and-Heroes/gameplay/the-basics.html)

## Quick start

The site is a collection of static HTML files. To browse everything locally:

1. From the repository root, start a simple web server (any static file server works). For example:

   ```bash
   python -m http.server 8000
   ```

2. Open `http://localhost:8000/point-counter.html` in your browser. This page wires up the JavaScript needed for the character builder and provides links to other content.

### Running tests in the browser

Automated tests live alongside the app scripts and are executed in the browser:

1. With the web server running, open `point-counter.html` in your browser.
2. Scroll to the bottom and click **Test All** (or enter `TestRunner.testAll();` in the command box) to run the full suite. Results appear in the `testResults` textarea near the bottom of the page.

See the [project plan](PROJECT_PLAN.md) for current priorities and follow-up tasks.
