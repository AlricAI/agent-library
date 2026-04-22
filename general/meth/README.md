# Meth

> +++
date = "2016-03-08T20:46:38Z"
title = "Project 4: Meth"

+++


This is another simple android application. It does one thing 
It keeps your phone 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
+++
date = "2016-03-08T20:46:38Z"
title = "Project 4: Meth"

+++


This is another simple android application. It does one thing 
It keeps your phone awake.

<!--more-->


For some applications we need to keep the phone awake no matter what. This application is an implementation of that.

You can find the code here [Meth](https://github.com/ernan/meth "Meth")

The GUI uses this really cool progress [https://github.com/Todd-Davies/ProgressWheel](https://github.com/Todd-Davies/ProgressWheel "ProgressWheel") by Todd Davis

This app builds upon a lot of the posts I have already made.

The app uses [EventBus](http://github.com/greenrobot/EventBus "EventBus") to handle user events.

It also uses the [Image Script](blog/image_script.md) to generate the resource images.


Essentially the application is a keep awake service that can be paused and restarted.
In general I would see this app as a support application to another application for example if you wanted to turn your phone into a 
security camera you could run this app in the background keeping your phone awake until it runs low on battery.

The Main class consists of a progress wheel which is updated by the service.
It uses a BroadcastReciever to communicate with the service.

```java

    private BroadcastReceiver broadcastReceiver = new BroadcastReceiver() {
        @Override
        public void onReceive(Context context, Intent intent) {
            Bundle b = intent.getExtras();
            long totalTime = b.getLong(Util.DURATION);
            Spanned text = Html.fromHtml("<font color=\"#CF000F\">Awake " + DateTimeUtil.formatTime(totalTime / 1000) + "</font>");
            if (!pw.isSpinning()) {
                pw.spin();
            }
            pw.setText(text.toString());

            Intent i = new Intent(MainActivity.this, NotificationReceiverActivity.class);
            PendingIntent pIntent = PendingIntent.getActivity(MainActivity.this, 0, i, 0);
            Notification notification = new Notification.

*[truncated — see source for full prompt]*