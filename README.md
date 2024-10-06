## setup-nuget

> Also installs `mono`

I use `nuget` in my GitHub CI , and that stopped working one day with the error `nuget: command not found`. I use commands that aren't available through `dotnet nuget`, so installing `nuget` seems to be the easiest solution.

Now (maybe always?) that requires `mono`, and so the installation became a bit complicated and decided to put it in a separate repo. Here it is:
```yaml
jobs:
  nuget-setup:
    runs-on: ubuntu-latest
    steps:
      - uses: JeroenBos/setup-nuget@v1
      - run: nuget help
```

Unfortunately installing `mono` takes very long (~50s), but it really is a prerequisite to `nuget`. I might look into optimizing that one day...
