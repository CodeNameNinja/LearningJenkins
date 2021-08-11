## Redirects and Variables

Lets create a variable in the `Execute shell` section and use it.

```bash
Name=Mitchell
echo "Hi $Name. current date and time is $(date)"
```

Okay that works, but what if we want to redirect the output of this data to a file?

thats also really simple all we have to do is use the

```> <path>```

```bash
Name=Mitchell
echo "Hi $Name. current date and time is $(date) > /tmp/info"
```

lets verify with

`cat /tmp/info`

'Hi Mitchell. current date and time is Wed 11 Aug 2021 05:31:34 PM UTC'