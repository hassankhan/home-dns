# Home DNS

A DNS system for my home, using Pi-Hole and Unbound in a Docker Compose stack,
running on a Raspberry Pi Model 4B.

## Getting started

First, clone the repo and navigate to it in your terminal:

```bash
git clone https://github.com/hassankhan/home-dns
cd home-dns
```

The stack requires a `.env` file, copy the example and fill in the missing
values:

```bash
cp .env.example .env
```

Also, create a new file `/etc/hosts.mydomain` and enter any custom hostnames
you'd like to resolve (leave empty if none).

```env
ServerIP=<IP_OF_RASPBERRY_PI>
TZ=Europe/London
WEBPASSWORD=<PASSWORD_FOR_PI_HOLE_ADMIN>
DNS1=127.0.0.1#5053
DNS2=127.0.0.1#5053
```

Once the environment variables are set, we can bring up the stack:

```bash
docker-compose up -d
```

To enable DNSSEC validation, run the following:

```bash
docker-compose exec unbound unbound-anchor -v
```
