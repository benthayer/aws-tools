# aws-tools

This is a small set of commands that I made to help me work with AWS more productively.
Feel free to submit your own pull requests and add to it!

Right now, the main functionality is to start and stop aws instances quickly via the command line while you're developing. I know sometimes I want a dev machine that's more powerful than my current computer, so but I only want it for a bit. These commands allow you to easily start and stop large instances. 

## How to use
To use this, it is assumed that you have already set up the AWS CLI.

One file of interest is `aws.json`, which is to be put in the same directory as the rest of these tools. 
You can of course change the commands to point to a different file locatoin.
`aws.json` is a simple key/value dictionary where you should have `"nickname": "instance-id"`. You make the nickname and use it in the various commands

By running `awscron`, you'll add an entry to your cronfile that will automatically shut down the server after 1 hour of no use.
It checks every minute, so if you don't log in immediately, it is likely that your instance will shut down before you can log in.
See #1 for details.

The most useful command is `sshaws` to be used like follows `sshaws myt2large`.
It will automatically look up the ip address of your instance and connect to it.

`awsdns` is also an interesting command. You run it like `awsdns myt2large`.
Right now, I have it set to modify my personal DNS server.
I do this because once I have the DNS set, I can use VSCode to route ssh into `ec2-user@myt2large.aws.benthayer.com`.
To use this command, you'll need a `.dns_env` file in your home directory.
`awsdns` has only been tested with my personal [mail-in-a-box](https://github.com/mail-in-a-box/mailinabox) server.
If you'd like to update it, look at issue #2

## Contributing
I'd appreciate any contributions.
I made this because it was useful for me.
Hopefully, it can be useful for more people!