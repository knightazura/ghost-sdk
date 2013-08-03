```
    /**
     * Example of how to add a persistent notification.
     */
    // $(document).on('click', '.add-persistent-notification', function (event) {
    //     event.preventDefault();
    //     var msg = {
    //             type: 'error',
    //             message: 'This is an error',
    //             status: 'persistent',
    //             id: 'per-' + $('.notification-persistent').length + 1
    //         };

    //     $.ajax({
    //         type: "POST",
    //         url: '/api/v0.1/notifications/',
    //         data: msg
    //     }).done(function (result) {
    //         var fcv;
    //         fcv = new Ghost.Views.FlashCollectionView({
    //             model: [msg]
    //         });
    //         console.log(fcv);
    //     });
    // });
```