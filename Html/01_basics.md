## async Attribute
The script loads asynchronously while the HTML is being parsed.

Once loaded, it pauses the HTML parsing and executes the script immediately.

Suitable for independent scripts that don’t rely on the DOM structure.

Loads the script asynchronously.
Executes immediately after loading.
HTML parsing pauses while the script runs.
Order of execution is not guaranteed (scripts may execute in any order).


## defer Attribute
The script loads asynchronously, but execution is deferred until the HTML is fully parsed.

Ensures that scripts are executed in order after the DOM is completely loaded.

Ideal for scripts that manipulate the DOM.

Loads the script asynchronously.
Executes only after HTML parsing is complete.
Execution order is maintained if multiple defer scripts are used.
Best for scripts that interact with the DOM.

## Replaced vs Non-Replaced Inline Elements
Replaced Inline Elements
Content is replaced by external data (image, media, form controls).

Accepts width and height.

Browser controls rendering.

Examples: <img>, <video>, <audio>, <input>, <iframe>.

Non-Replaced Inline Elements
Pure text-based elements directly rendered by the browser.

Does not accept width and height (unless display: inline-block).

Examples: <span>, <a>, <b>, <i>, <u>.