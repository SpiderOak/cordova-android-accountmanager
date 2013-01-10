cordova-android-accountmanager
==============================

Introduction
------------

cordova-android-accountmanager is an [Android](https://github.com/android) [AccountManager](http://developer.android.com/reference/android/accounts/AccountManager.html) plugin for [cordova-android](https://github.com/apache/cordova-android).

It currently only supports explicit account handling (programatically adding/removing/settin/getting account details to the AccountManager).


Basic Usage (Explicit account handling)
-------

	var am = window.plugins.accountmanager;

	// Add account explicitly
	am.addAccountExplicitly('MyAccountType', 'bob', 'passwordbob', function(error, bob)
	{
		// bob.name = 'bob'
		// bob.type = 'MyAccountType'

		// List all accounts of MyAccountType
		am.getAccountsByType('MyAccountType', function(error, accounts)
		{
			accounts.forEach(function(account)
			{
				console.log('Account: ' + JSON.stringify(account));
			});
		});

		// Get password
		am.getPassword(bob, function(error, password)
		{
			console.log("Bob's password: " + password);
		});

		// Get/Set user data
		am.setUserData(bob, 'age', 30);
		am.getUserData(bob, 'age', function(error, age)
		{
			console.log('Bob is ' + age + 'years old');
		});

		// Remove account
		am.removeAccount(bob);
	});

Basic Usage (Authenticator based handling)
-----

	Not yet supported.