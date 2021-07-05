# iDetailAid HTML Slider Example
This HTML package allows you to create a custom interactive slider that can trigger actions/code in the slide code editor, or set session data directly.

Placing more of the logic in the slide code editor gives you greater flexibility allowing the HTML package to be re used multiple times in the same slide, or across different slides / presentations.

#  Events / Actions
HTML packages in a iDetailAid can send events and trigger actions in the containing slide.  You can either listen for the events directly via code in the slide code editor, or you can expose names actions to appear in the actions drop down menu for non technical users.

# Docs
For more information see the following hep docs.

[Slide code editor](https://docs.idetailaid.co.uk/dev-docs/code-editor/)   

[HTML Packages, events, actions](https://docs.idetailaid.co.uk/dev-docs/html-packages/)  

[Saving data between slides](https://docs.idetailaid.co.uk/dev-docs/persist-data/)   

[Rendering dynamic data in the slide](https://docs.idetailaid.co.uk/dev-docs/persist-data/)  



# Listening for the Events.
## Code Editor
In this example the HTML package triggers a `sliderChange` event.  To listen for this, first give the content area in iDetailAid a `name`.    

Click on the content area holding this HTML package and choose the `General` tab in the properties panel, then enter a name.  

In the code editor for the slide, you can add the following code to save it in local storage. Deselect the content area, and the click the `Code Editor` tab in the properties panel.

```
$slide.on('sliderChange', '#my_slider_name', (event) => {
    window.localStorage.setItem('sliderValue', event.detail);
});
```

It can then be read in a subsequent slide with.

```
$slide.on('slideShown', (event) => {
    const sliderValue = window.localStorage.getItem('sliderValue');
});
```

It can also be used directly in a text area with some [templating tags](https://docs.idetailaid.co.uk/dev-docs/persist-data/).


The following text in a text area would render the slide value.

```
"Hello, the slide value is {{ls.sliderValue}}"
```

## Actions Menu
If you declare the events in the [manifest.json](https://docs.idetailaid.co.uk/dev-docs/html-packages/#the-manifestjson-file) file, then a non technical user can select that as an `Action` in the iDetailAid editor.

They can then pick the corresponding action to trigger, such as Navigate to a slide, using the user interface, rather than code.




