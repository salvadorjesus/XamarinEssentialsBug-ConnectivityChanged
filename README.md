# XamarinEssentialsBug-ConnectivityChanged

A repo to demonstrate a bug in Xamarin Essentials.

# Description

`Connectivity.ConnectivityChanged` handler does not work when targeting API 34 on Android 14 phones.

With other combinations of API levels and Android version it seems to work.

This is the same bug already reported and fixed in Maui: [Adding a Connectivity.ConnectivityChanged handler does not work on Android 14 #19949](https://github.com/dotnet/maui/issues/19949).

# Project overview
This is a basic template Xamarin project. In App.xaml.cs i have added the following in the constructor:
```
Connectivity.ConnectivityChanged += Connectivity_ConnectivityChanged;
```

And the following method:
```
        private async void Connectivity_ConnectivityChanged(object sender, ConnectivityChangedEventArgs e)
        {
            Console.WriteLine("Connectivity changed");
        }
```
# Stepts to reproduce
Download and compile this project targeting API 33 or run it in an Android 13 emulator. When you make change on the connectivity (switch flight mode on and off), the line 'connectivity changed' appears on the console.

When compiling for API 34 *and* running in an Android 14 emulator, nothing appears on console (`Connectivity_ConnectivityChanged` is never reached).

# Nugget versions
Latest on release date:

* Xamarin Forms: 5.0.0.2622.
* Xamarin Essentials: 1.8.1
