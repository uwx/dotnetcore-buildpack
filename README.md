# Heroku .NET Core Buildpack

Heroku buildpack for .NET Core 2.1 console applications.

[![Build status](https://ci.appveyor.com/api/projects/status/5864d533m5d35nsa?svg=true)](https://ci.appveyor.com/project/jincod/dotnetcore-buildpack)


## Usage

```bash
heroku buildpacks:set https://github.com/uwx/dotnetcore-buildpack
```

Add to your Procfile:
```
dyno: cd $HOME/ProjectName && ls -l && ../heroku_output/ProjectName
```

And make a Projfile marking the main project:
```
ProjectName/ProjectName.csproj
```

More info

- [Buildpack references](https://devcenter.heroku.com/articles/buildpacks#buildpack-references)

## Using MyGet and other external NuGet package sources

This buildpack doesn't look for NuGet config files outside of the root folder by default. Your config folder is probably in the `.nuget` directory, so you can copy it there or make your own fork of the buildpack, adding this line:
```bash
cp ${BUILD_DIR}/.nuget/NuGet.config ${BUILD_DIR}/NuGet.config
```
