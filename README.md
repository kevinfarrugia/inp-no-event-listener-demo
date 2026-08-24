# INP No Event Listener Demo

A simple demo that registers a long interaction time for an interaction that does not have an event listener. In this demo, we are using a checkbox and CSS to update the UI following an interaction. The page includes a recurring JavaScript main thread delay to throttle the CPU and keep the main thread busy.

## Instructions

- Open [index.html](https://kevinfarrugia.github.io/inp-no-event-listener-demo/) in the browser.
- Clicking on the _Show Overlay_ label will trigger a full screen overlay.

<img width="1268" height="569" alt="Screenshot of the Chrome DevTools Performance Panel showing two long interactions" src="https://github.com/user-attachments/assets/b973b298-01b1-4ed7-af1c-e530300bd88f" />

In the preceding screenshot of Chrome DevTools, there are two interactions with the page that register a lengthy input delay and a processing duration of 0 ms resulting in a long interaction and a high [Interaction to Next Paint (INP)](https://developer.mozilla.org/en-US/docs/Glossary/Interaction_to_next_paint)

## Specification

According to the [W3C Event Timing API](https://www.w3.org/TR/event-timing/) specification, an interaction is defined as a collection of event entries that share the same `interactionId` generated following a user action. The possible user actions include clicking, tapping, keyboard interactions, and dragging of content. Scrolling, pinch-to-zoom, hover, and focus events are excluded. Additionally, a user interaction could also occur on a non-interactive element. In our example, the label does not have an event handler and is therefore considered "non-interactive". Nonetheless, according to the spec it should still be treated as an interaction.
