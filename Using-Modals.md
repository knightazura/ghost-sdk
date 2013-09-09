### Building a Modal

First you need to define the content in an content related named `.hbs` file. For example `markdown-help.hbs`.

In this file place the contents of the modal.

### Triggering The Modal
Information comments with a `*` indicate optional.
#### Information Modal

```
this.addSubview(new Ghost.Views.Modal({
    model: {
        options: {
            close: true, // Is the close icon visible
            type: "info", // * The type of modal
            style: ["wide"], // * Additional modal styles
            animation: 'fade' // * The animation effects on the modal
        },
        content: {
            template: 'content-file', // The content file without the extension
            title: 'An appropriate title' // Title displayed in the modal
        }
    }
}));
```


#### Action Modal

```
this.addSubview(new Ghost.Views.Modal({
    model: {
        options: {
            close: false, // Is the close icon visible
            confirm: {
                accept: {
                    func: function () { // The function called on acceptance
                        console.log("accepted");
                    },
                    text: "Yes" // The accept button text
                },
                reject: {
                    func: function () { // The function called on rejection
                        console.log("rejected");
                    },
                    text: "No" // The reject button text
                }
            },
            type: "action", // * The type of modal
            animation: 'fade'
        },
        content: {
            template: 'content-file', // The content file without the extension
            title: 'An appropriate title' // Title displayed in the modal
        }
    }
}));
```

##### Reference


* `type`: By default either `action` or `info`, but others can be specfied in the SCSS by using:
```
.modal-{{type}} {
    @extend %modal;
    ...
}
```

* `style`: These are extra classes that can be used to add visual styles across the modal. These can be specified in the SCSS by using:
```
.modal-style-{{style}} {
    @extend %modal;
    ...
}
```

* `animation`: These are animations for the modal to appear with. Currently there is only `fadeIn`.