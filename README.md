# @argos-ci/cypress

[Cypress](https://cypress.io) commands and utilities for [Argos](https://argos-ci.com) visual testing.

## Installation

```sh
npm install --save-dev @argos-ci/cypress
```

And add this line to your `cypress/support/index.js` file.

```js
import "@argos-ci/cypress/support";
```

## Usage

`cy.argosScreenshot` - command stabilizes the UI and takes a screenshot.

_How to take a screenshot with `cy.argosScreenshot` command_

```js
describe("Homepage", () => {
  it("should be stable", () => {
    // Screenshot a full page
    cy.argosScreenshot("home");

    // Screenshot a component
    cy.get("main div.breadcrumb").argosScreenshot("home-breadcrumb");
  });
});
```

### Configuration

`cy.argosScreenshot([name][, options])`

- `name` - The screenshot name; must be unique; default value to test title
- `options` - Send to [cy.screenshot command options](https://docs.cypress.io/api/commands/screenshot)

## Helper props

The helpers props can be used to improve screenshots stability.

- `[data-visual-test="transparent"]` - Make it transparent to Argos (`opacity: 0`)
- `[data-visual-test="removed"]` - Remove the element from Argos (`display: none`)

_How to use an helper to hide a div from a screenshot_

```html
<div id="clock" data-visual-test="transparent">
  <!-- the clock code -->
</div>
```