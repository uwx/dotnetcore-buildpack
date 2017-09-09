# Heroku .NET Core Buildpack

Heroku buildpack for .NET Core 2.0.0 console applications. This builds the first solution it can find.

## Usage

For Heroku-16 stack and .NET Core 2.0.0

```bash
heroku buildpacks:set https://github.com/uwx/dotnetcore-buildpack
```

Add to your Procfile:
```
dyno: cd $HOME/heroku_output && ./SolutionName
```

More info

- [Buildpack references](https://devcenter.heroku.com/articles/buildpacks#buildpack-references)
- [Heroku-16 Stack](https://devcenter.heroku.com/articles/heroku-16-stack)

## Using MyGet and other external NuGet package sources

This buildpack doesn't look for NuGet config files outside of the root folder by default. Your config folder is probably in the `.nuget` directory, so you can copy it there or make your own fork of the buildpack, adding this line:
```bash
cp ${BUILD_DIR}/.nuget/NuGet.config ${BUILD_DIR}/NuGet.config
```
