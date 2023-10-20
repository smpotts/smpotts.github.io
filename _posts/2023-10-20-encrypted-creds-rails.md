---
layout: post
title: Encrypted Credentials in Rails
subtitle: A simple and safe way to store project credentials
cover-img: /assets/img/fall.jpeg
thumbnail-img: /assets/img/fall.jpeg
share-img: /assets/img/fall.jpeg
tags: [ruby, ruby_on_rails, security]
---

I recently encountered [Encrypted Credentials](https://edgeguides.rubyonrails.org/security.html#custom-credentials) in Ruby on Rails as a method for storing encrypted credentials in your Rails project. It allows you to store and edit important credentials needed by your application without having to check passwords in plain text, and it makes it easier to share the credentials with other teammates who might need them.

The setup for Rails encrypted credentials is pretty simple. It supports having one single credentials file for the project, or splitting the credentials files out by environment (i.e. one for development, staging, and production). To create the an encrypted credentials file for your project, specify which editor you want to use and run the following:
```
EDITOR:"vi --wait" bin/rails credentials:edit
```

If you wanted to do this per environment (for production for example), it would look like:
```
EDITOR:"vi --wait" bin/rails credentials:edit --environment production
```
This will create a credentials folder and an encrypted credentials file under the config directory in the project root. Inside the credentials folder you will see the encrypted yml file `credentials.yml.enc` and a corresponding `master.key` file with the master password to decrypt the credentials file. Rails also takes care of putting the `master.key` file in the `.gitignore` file so it doesn't get checked in by accident.

When you are ready to edit the credentials file, you can do so by running:
```
EDITOR="vi" rails credentials:edit
```
The yml file will open for editing. After you save and write any changes, it will exit with a statement showing the changes were successful:
```
File encrypted and saved.
```

Then if you want to retrieve values out of the encrypted credentials file, all you have to do is start a rails console and retrieve a credential from the yml file like this:
```
Rails.application.credentials.mysecretcred[:password]
```

Using Rails built in handling for encrypted credentials is a great tool for securing credentials for Rails applications.
