# Android Settings

> +++
date = "2016-01-31T00:08:26Z"
title = "An android SharedPreferences wrapper class"

+++

This is a wrapper around the Android [SharedPreferences](

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
+++
date = "2016-01-31T00:08:26Z"
title = "An android SharedPreferences wrapper class"

+++

This is a wrapper around the Android [SharedPreferences](http://developer.android.com/reference/android/content/SharedPreferences.html "SharedPreferences")

It adds a few useful extensions

<!--more-->

1. It allows you to store lists of strings, integers etc.
2. It allows you to store a Bitmap



You can find the code here [DB.java](https://gist.github.com/ernan/098dcc1a58311675b472 "DB.java")


```java

import android.content.Context;
import android.content.SharedPreferences;
import android.graphics.Bitmap;
import android.os.Environment;
import android.preference.PreferenceManager;
import android.text.TextUtils;

import java.io.File;
import java.io.FileOutputStream;
import java.io.IOException;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Map;

public class DB {
    private static final String SEP = "‚‗‚";
    private static final String IMAGE_DATA_DIRECTORY = "ImageCache";
    private static final String LAST_SEARCH_TIME = "LAST_SEARCH_TIME";

    Context mContext;
    SharedPreferences mSharedPreferences;
    File mFolder = null;

    public DB(Context context) {
        mContext = context;
        mSharedPreferences = PreferenceManager.getDefaultSharedPreferences(mContext);
    }

    public int getInt(String key) {
        return getInt(key, 0);
    }

    public int getInt(String key, int defaultValue) {
        return mSharedPreferences.getInt(key, defaultValue);
    }

    public long getLong(String key) {
        return getLong(key, 0L);
    }

    public long getLong(String key, long defaultValue) {
        return mSharedPreferences.getLong(key, defaultValue);
    }

    public String getString(String key) {
        return getString(key, "");
    }

    public String getString(String key, String defaultValue) {
        return mSharedPreferences.getString(key, defaultValue);
    }

    public double getDouble(String key) {
        return get

*[truncated — see source for full prompt]*