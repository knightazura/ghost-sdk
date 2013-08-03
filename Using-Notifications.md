## Description
There are two kinds of notifications: persistent and passive. Both of them can be added from the client side and the server side.

Persistent notifications won't disappear until you manually dismiss them with the close button. Passive notifications will go away when there's a new notification, or when you navigate away, or when you dismiss them. In case of a `success` notification (green one), it will disappear automatically.

Passive notifications are conjured up through backbone.js. Persistent notifications are conjured up with backbone.js, and also added to the `ghost.notifications` as an array of objects.

## Structure
This is the model for the notifications:
```
msg = {
    type: 'error', // this can be 'error', 'success', 'warn' and 'info'
    message: 'This is an error', // A string. Should fit in one line.
    status: 'persistent', // or 'passive'
    id: 'auniqueid' // A unique ID
};
```

## How to add them
### Server side
Assuming `object` is a notification (see above): `ghost.notifications.push(object);`

## Client side

Everything you need to know is in the next code snippet:
```
/**
 * Example of how to add a persistent notification.
 */
$(document).on('click', '.add-persistent-notification', function (event) {
    event.preventDefault();
    var msg = {
            type: 'error',
            message: 'This is an error',
            status: 'persistent',
            id: 'per-' + $('.notification-persistent').length + 1
        };
    $.ajax({
        type: "POST",
        url: '/api/v0.1/notifications/',
        data: msg
    }).done(function (result) {
        var fcv;
        fcv = new Ghost.Views.FlashCollectionView({
            model: [msg]
        });
        console.log(fcv);
    });
});
```

The server then takes the object, pushes it to the `ghost.notifications`, and gives you back a success result, which means the client can then make the notification appear without you having to wait until next navigation.