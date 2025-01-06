# {py:mod}`abx_plugin_ripgrep_search.config`

```{py:module} abx_plugin_ripgrep_search.config
```

```{autodoc2-docstring} abx_plugin_ripgrep_search.config
:allowtitles:
```

## Module Contents

### Classes

````{list-table}
:class: autosummary longtable
:align: left

* - {py:obj}`RipgrepConfig <abx_plugin_ripgrep_search.config.RipgrepConfig>`
  -
````

### Data

````{list-table}
:class: autosummary longtable
:align: left

* - {py:obj}`RIPGREP_CONFIG <abx_plugin_ripgrep_search.config.RIPGREP_CONFIG>`
  - ```{autodoc2-docstring} abx_plugin_ripgrep_search.config.RIPGREP_CONFIG
    :summary:
    ```
````

### API

`````{py:class} RipgrepConfig(_case_sensitive: bool | None = None, _nested_model_default_partial_update: bool | None = None, _env_prefix: str | None = None, _env_file: pydantic_settings.sources.DotenvType | None = ENV_FILE_SENTINEL, _env_file_encoding: str | None = None, _env_ignore_empty: bool | None = None, _env_nested_delimiter: str | None = None, _env_parse_none_str: str | None = None, _env_parse_enums: bool | None = None, _cli_prog_name: str | None = None, _cli_parse_args: bool | list[str] | tuple[str, ...] | None = None, _cli_settings_source: pydantic_settings.sources.CliSettingsSource[typing.Any] | None = None, _cli_parse_none_str: str | None = None, _cli_hide_none_type: bool | None = None, _cli_avoid_json: bool | None = None, _cli_enforce_required: bool | None = None, _cli_use_class_docs_for_groups: bool | None = None, _cli_exit_on_error: bool | None = None, _cli_prefix: str | None = None, _cli_flag_prefix_char: str | None = None, _cli_implicit_flags: bool | None = None, _cli_ignore_unknown_args: bool | None = None, _secrets_dir: pydantic_settings.sources.PathType | None = None, **values: typing.Any)
:canonical: abx_plugin_ripgrep_search.config.RipgrepConfig

Bases: {py:obj}`abx_spec_config.base_configset.BaseConfigSet`

````{py:attribute} RIPGREP_BINARY
:canonical: abx_plugin_ripgrep_search.config.RipgrepConfig.RIPGREP_BINARY
:type: str
:value: >
   'Field(...)'

```{autodoc2-docstring} abx_plugin_ripgrep_search.config.RipgrepConfig.RIPGREP_BINARY
```

````

````{py:attribute} RIPGREP_IGNORE_EXTENSIONS
:canonical: abx_plugin_ripgrep_search.config.RipgrepConfig.RIPGREP_IGNORE_EXTENSIONS
:type: str
:value: >
   'Field(...)'

```{autodoc2-docstring} abx_plugin_ripgrep_search.config.RipgrepConfig.RIPGREP_IGNORE_EXTENSIONS
```

````

````{py:attribute} RIPGREP_ARGS_DEFAULT
:canonical: abx_plugin_ripgrep_search.config.RipgrepConfig.RIPGREP_ARGS_DEFAULT
:type: typing.List[str]
:value: >
   'Field(...)'

```{autodoc2-docstring} abx_plugin_ripgrep_search.config.RipgrepConfig.RIPGREP_ARGS_DEFAULT
```

````

````{py:attribute} RIPGREP_SEARCH_DIR
:canonical: abx_plugin_ripgrep_search.config.RipgrepConfig.RIPGREP_SEARCH_DIR
:type: pathlib.Path
:value: >
   None

```{autodoc2-docstring} abx_plugin_ripgrep_search.config.RipgrepConfig.RIPGREP_SEARCH_DIR
```

````

````{py:attribute} RIPGREP_TIMEOUT
:canonical: abx_plugin_ripgrep_search.config.RipgrepConfig.RIPGREP_TIMEOUT
:type: int
:value: >
   'Field(...)'

```{autodoc2-docstring} abx_plugin_ripgrep_search.config.RipgrepConfig.RIPGREP_TIMEOUT
```

````

`````

````{py:data} RIPGREP_CONFIG
:canonical: abx_plugin_ripgrep_search.config.RIPGREP_CONFIG
:value: >
   'RipgrepConfig(...)'

```{autodoc2-docstring} abx_plugin_ripgrep_search.config.RIPGREP_CONFIG
```

````