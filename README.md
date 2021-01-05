# Pulumi Local
A Pulumi provider built from Terraform Local, which creates local files.
## Local Development
```
make build

tmpdir=$(mktemp -d)
cp bin/pulumi-resource-local $tmpdir

# TODO: You can use -C with `tar` so you don't have to `cd`
cd $tmpdir
tar -czf pulumi-resource-local.tar.gz .

pulumi plugin install resource local VERSION --file=pulumi-resource-local.tar.gz
```

Then, in another Pulumi project
```
yarn link @pulumi/local
```

Now you can use it like you normally would.

## Tips
- Use `pulumi plugin` to help you debug. If you think there is something wrong with a tarball you generated, go look (~/.pulumi/plugins) at the resulting plugin that was installed. It should have the same format as the other plugins you have locally, which work.
- Use the naming convention `pulumi-<name> == terraform-provider-<name>`. If you break this there's more you'll have to do.

# TODO
- [ ] What's the difference between a resource and a data source?
- [ ] How can I set the version so it's done with `make build`, or another make command?
- [ ] Create a make command that only does nodejs
- [ ] Experiment with custom package names
- [ ] Should we, or should we not commit the generated SDK?



# Notes
## Naming Convention


If you break this you have more work in store for yourself.

