# [Mozubi - Learning platform](https://www.mozubi.app/)

## License

All source code in the [Mozubi](https://www.mozubi.app/)
is available under the NAME License.

## Getting started

To get started with the app, clone the repo and then install the needed gems:

```shell
$ bundle install
```

Next, migrate the database:

```shell
$ rails db:migrate
```

Finally, run the test suite to verify that everything is working correctly:

```shell
$ rails test
```

If the test suite passes, you'll be ready to run the app in a local server:

```shell
$ rails server
```

## Development

### Git

Clone the repo.
Master branch is the official page online. Branch from the master branch only for hotfixes.
For development branch out of development branch, add new features, push you branch to github, make a pull request to development branch.
The development branch is online - [staging app](https://mozzubi-staging.herokuapp.com/).

## Email in development

To simulate email sending in development we use letter_opener. For this to work you need to run in another terminal tab:

```shell
$  redis-cli FLUSHALL # clear queue
$ bundle exec sidekiq --environment development  -t 25
```

### Automate tests with guard

```shell
# prepare db
$ rake db:test:prepare RAILS_ENV=test
$ bin/spring stop    # Try this if the tests mysteriously start failing.
$ bundle exec guard
```

### Pull db data from heroku

```shell
$ todo
```

### Check security with brakeman

```shell
$ bundle exec brakeman
```

### Check gem vulnerabilities with bundle-audit

```shell
$ bundle exec bundle-audit
```

### Pundit. Use the supplied generator to generate policies

```shell
rails g pundit:policy model
```

### rack-mini-profiler

```shell
bundle exec rails g rack_profiler:install
```

### Flamegraphs

To generate flamegraphs visit a page in your app with ?pp=flamegraph

### Memory Profiling

Memory allocations can be measured (using the memory_profiler gem) which will show allocations broken down by gem, file location, and class and will also highlight String allocations.

Add ?pp=profile-memory to the URL of any request while Rack::MiniProfiler is enabled to generate the report.

Additional query parameters can be used to filter the results.

memory_profiler_allow_files - filename pattern to include (default is all files)
memory_profiler_ignore_files - filename pattern to exclude (default is no exclusions)
memory_profiler_top - number of results per section (defaults to 50)
The allow/ignore patterns will be treated as regular expressions.

Example: ?pp=profile-memory&memory_profiler_allow_files=active_record|app

There are two additional pp options that can be used to analyze memory which do not require the memory_profiler gem

Use ?pp=profile-gc to report on Garbage Collection statistics
Use ?pp=analyze-memory to report on ObjectSpace statistics

## Test coverage

Uncomment simplecov in test_helper.rb
After running your tests, open coverage/index.html in the browser of your choice.

on mac: open coverage/index.html

in a debian/ubuntu Terminal: xdg-open coverage/index.html

### Error handling

[airbrake](https://airbrake.io/)
