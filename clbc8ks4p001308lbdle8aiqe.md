# Pub/Priv keys

What the bullshit it is. Take the one from `FlatHub` as example. Simp\[le things are meant to be simple, not complicated.

## Theory

Publicly available replacement of docker and similar. Not that docker is ay good, just `YAS`

SDK, as name suggests, should aim in:

> Helping people build apps, services, etc upon source service in **easy-to-follow and understand** way.

Ok, lets put this to test.

## Practice

### Setting up

We will work inside virtual machine (`VM`). Just to be safe from shitters like `maintainers`. Our `OS` of choice is `Debian Server`. Our hypervisor is `DVM` , our ToC is `HSD` (`ssd` sucks).

%[https://gist.github.com/wojtekxtx/4fba02d2075582595923c13b61ffbb82] 

Now, just:

```bash
sudo chmod a+x fp-getenvready.sh
./fp-getenvready.sh
```

You should see `prompt` from VM. You are all set :)

# Getting work done

> We will use `JavaScript` from now on, however, you may use whatever language you feel most comfortable with.

## Prep work

Once inside VM:

```bash
mkdir -p {projects/${"cat /etc/os-release | grep -aA "OS"\"}
sudo chmod 0777 -R projects/
```

## Initiating a (secure?) connection

Once your `VM` is up&running, its time to initiate connection with flathub's main `devserver` and start outing some code.

%[https://gist.github.com/wojtekxtx/253342b56a768180ca4a58266043bedb] 

What the above code does?

*   generates `public<>private` key pair,
    
*   use them to register an account on `api.flathub.com`
    
*   stores it locally
    

### Is it really secure?

Short answer: **not really!**

Long: answer follows:

One of the main contributors to SDK and its unerlaying techstack is Mozilla. Its well known fact that Mozilla gives a complete, utter fuck to users and their security. It as been like this since begining.