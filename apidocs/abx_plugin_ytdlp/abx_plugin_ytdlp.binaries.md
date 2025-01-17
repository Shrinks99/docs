# {py:mod}`abx_plugin_ytdlp.binaries`

```{py:module} abx_plugin_ytdlp.binaries
```

```{autodoc2-docstring} abx_plugin_ytdlp.binaries
:allowtitles:
```

## Module Contents

### Classes

````{list-table}
:class: autosummary longtable
:align: left

* - {py:obj}`YtdlpBinary <abx_plugin_ytdlp.binaries.YtdlpBinary>`
  -
* - {py:obj}`FfmpegBinary <abx_plugin_ytdlp.binaries.FfmpegBinary>`
  -
````

### Data

````{list-table}
:class: autosummary longtable
:align: left

* - {py:obj}`YTDLP_BINARY <abx_plugin_ytdlp.binaries.YTDLP_BINARY>`
  - ```{autodoc2-docstring} abx_plugin_ytdlp.binaries.YTDLP_BINARY
    :summary:
    ```
* - {py:obj}`FFMPEG_BINARY <abx_plugin_ytdlp.binaries.FFMPEG_BINARY>`
  - ```{autodoc2-docstring} abx_plugin_ytdlp.binaries.FFMPEG_BINARY
    :summary:
    ```
````

### API

`````{py:class} YtdlpBinary(/, **data: typing.Any)
:canonical: abx_plugin_ytdlp.binaries.YtdlpBinary

Bases: {py:obj}`abx_pkg.Binary`

````{py:attribute} name
:canonical: abx_plugin_ytdlp.binaries.YtdlpBinary.name
:type: abx_pkg.BinName
:value: >
   None

```{autodoc2-docstring} abx_plugin_ytdlp.binaries.YtdlpBinary.name
```

````

````{py:attribute} binproviders_supported
:canonical: abx_plugin_ytdlp.binaries.YtdlpBinary.binproviders_supported
:type: typing.List[pydantic.InstanceOf[abx_pkg.BinProvider]]
:value: >
   None

```{autodoc2-docstring} abx_plugin_ytdlp.binaries.YtdlpBinary.binproviders_supported
```

````

`````

````{py:data} YTDLP_BINARY
:canonical: abx_plugin_ytdlp.binaries.YTDLP_BINARY
:value: >
   'YtdlpBinary(...)'

```{autodoc2-docstring} abx_plugin_ytdlp.binaries.YTDLP_BINARY
```

````

`````{py:class} FfmpegBinary(/, **data: typing.Any)
:canonical: abx_plugin_ytdlp.binaries.FfmpegBinary

Bases: {py:obj}`abx_pkg.Binary`

````{py:attribute} name
:canonical: abx_plugin_ytdlp.binaries.FfmpegBinary.name
:type: abx_pkg.BinName
:value: >
   'ffmpeg'

```{autodoc2-docstring} abx_plugin_ytdlp.binaries.FfmpegBinary.name
```

````

````{py:attribute} binproviders_supported
:canonical: abx_plugin_ytdlp.binaries.FfmpegBinary.binproviders_supported
:type: typing.List[pydantic.InstanceOf[abx_pkg.BinProvider]]
:value: >
   None

```{autodoc2-docstring} abx_plugin_ytdlp.binaries.FfmpegBinary.binproviders_supported
```

````

````{py:attribute} overrides
:canonical: abx_plugin_ytdlp.binaries.FfmpegBinary.overrides
:type: abx_pkg.BinaryOverrides
:value: >
   None

```{autodoc2-docstring} abx_plugin_ytdlp.binaries.FfmpegBinary.overrides
```

````

`````

````{py:data} FFMPEG_BINARY
:canonical: abx_plugin_ytdlp.binaries.FFMPEG_BINARY
:value: >
   'FfmpegBinary(...)'

```{autodoc2-docstring} abx_plugin_ytdlp.binaries.FFMPEG_BINARY
```

````
