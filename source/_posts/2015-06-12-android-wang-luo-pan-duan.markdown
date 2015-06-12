---
layout: post
title: "Android 网络判断"
date: 2015-06-12 16:51:05 +0800
comments: true
categories: Android
---
总结一下在Android 中常用的网络判断代码。

判断是否有网代码如下：
{% codeblock lang:java  %}
public static boolean isNetworkAvailable(Context context) {
    ConnectivityManager mConnectivityManager = (ConnectivityManager)    
    context.getSystemService(Context.CONNECTIVITY_SERVICE);
    //这行代码需要权限android.permission.ACCESS_NETWORK_STATE
    //如果没有连接网络就会返回null
    NetworkInfo activeNetworkInfo = mConnectivityManager.getActiveNetworkInfo();
    if (activeNetworkInfo!=null) {
        //即使网络连接着，也可能没有网
        return activeNetworkInfo.isAvailable();
    }
    //没有网络连接
    return false;
}
{% endcodeblock %}

网络类型：
{% codeblock lang:java %}
public static final String NETWORK_TYPE_WIFI = "wifi";
public static final String NETWORK_TYPE_2G = "2G";
public static final String NETWORK_TYPE_3G = "3G";
public static final String NETWORK_TYPE_4G = "4G";
public static final String NETWORK_TYPE_UNKNOWN = "unknown";
{% endcodeblock %}

判断当前网络类型：
{% codeblock lang:java %}
public static String getNetworkType(Context context){
    ConnectivityManager mConnectivityManager = (ConnectivityManager)  
    context.getSystemService(Context.CONNECTIVITY_SERVICE);
    NetworkInfo activeNetworkInfo = mConnectivityManager.getActiveNetworkInfo();
    if(activeNetworkInfo==null){
        return NETWORK_TYPE_UNKNOWN;
    }
    //首先判断当前网络是WIFI连接还是MOBILE连接
    if (ConnectivityManager.TYPE_WIFI == activeNetworkInfo.getType()){
        return NETWORK_TYPE_WIFI;
    }else {
        return getNetworkClass(activeNetworkInfo.getSubtype());
    }

}

private static String getNetworkClass(int networkType) {
    switch (networkType) {
        case TelephonyManager.NETWORK_TYPE_GPRS:
        case TelephonyManager.NETWORK_TYPE_EDGE:
        case TelephonyManager.NETWORK_TYPE_CDMA:
        case TelephonyManager.NETWORK_TYPE_1xRTT:
        case TelephonyManager.NETWORK_TYPE_IDEN:
            return NETWORK_TYPE_2G;
        case TelephonyManager.NETWORK_TYPE_UMTS:
        case TelephonyManager.NETWORK_TYPE_EVDO_0:
        case TelephonyManager.NETWORK_TYPE_EVDO_A:
        case TelephonyManager.NETWORK_TYPE_HSDPA:
        case TelephonyManager.NETWORK_TYPE_HSUPA:
        case TelephonyManager.NETWORK_TYPE_HSPA:
        case TelephonyManager.NETWORK_TYPE_EVDO_B:
        case TelephonyManager.NETWORK_TYPE_EHRPD:
        case TelephonyManager.NETWORK_TYPE_HSPAP:
            return NETWORK_TYPE_3G;
        case TelephonyManager.NETWORK_TYPE_LTE:
            return NETWORK_TYPE_4G;
        default:
            return NETWORK_TYPE_UNKNOWN;
    }
}
{% endcodeblock %}

