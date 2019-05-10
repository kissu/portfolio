Some scripting linux tips or mementos I wish to keep in the long run.
Will probably make a blog post if there are enough commands.

```
ssh -A -R localhost:50000:bergerac-pasteur.scaso:22 tprint@saint-astier.scaso \
> 'rsync -e "ssh -p 50000 -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null" -av -P /home/tprint/easyplv/shared/dump_saint_astier_assets_february.tar.gz tprint@localhost:/home/tprint/dump_saint_astier_assets_february.tar.gz'
```
