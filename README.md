# Heroku aria2c

> Heroku banning account immediately after deploy.
> 29-08-2019 | 17:56

## Optionally sync downloaded file to your cloud drive with Rclone

1. Setup Rclone locally by following offical instructions: https://rclone.org/docs/
2. Find your `rclone.conf` file, it should look like this:

```conf
[DRIVENAME]
type = WHATEVER
client_id = WHATEVER
client_secret = WHATEVER
scope = WHATEVER
token = WHATEVER

others entries...
```

3. Find the drive you want to use, and copy its `type = ...` to  `... token = ...` section.
4. Encode it with [`Base64`](https://www.base64encode.org)
5. Deploy with the button above, and paste the string in `RCLONE_CONFIG`
6. Set `RCLONE_DESTINATION` to a path you want to store your downloaded files. `/` for root_folder.

## FAQ

### It automatically stop after 30 minutes, and files were lost.

It is because Heroku's free dyno will idle when there is no incoming request within 30 minutes, and your files will be deleted too, this is why you might want to use Rclone.

### Can I delete files?

No. Just wait for its idling, and your files will be deleted.

### You said it will idle automatically, so I can't download large files?

It will generate fake requests when there are downloading or uploading tasks, so it won't idle when your files aren't completed.

### I don't know how to setup Rclone, can you help me?

No. I thought the instructions above are enough.
