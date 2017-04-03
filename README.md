# django-endpoint

An end point to run Django services on.

## Installation

Start by downloading and building the project when necessary. The following
commands will do the job on most Debian based Linux distributions.

```bash
git clone https://github.com/mbp76/django-endpoint
cd django-endpoint
sudo ./gradlew
```

## Usage

The installation process will install the project dependencies and migrations.
An administration user will also be created from the Gradle build script
parameters. Run the command below and login at `http://127.0.0.1:8000/admin`.

```bash
sudo python manage.py runserver
```

To add a service module, start by declaring it in `settings.py` and include the
module's URL configuration in `urls.py`.

```python
INSTALLED_APPS = [
    ...
    'myservice',
]
```

```python
urlpatterns = [
    ...
    url(r'^myservice/', include('myservice.urls')),
]
```

## Testing

Test checks are executed automatically every time the project is built. Builds
can be done remotely or continuously on a development context. For continuous
integration and development use docker-compose. This is recommended to keep the
system clean while the project is built every time the sources change.

```bash
sudo docker-compose up
```

For continuous integration and development without any dependencies use the
Gradle wrapper. This is the best option if the wrapper is available and the
Docker context is not valid. For a full list of tasks, see
`sudo ./gradlew tasks --all`. For a CI cycle use `sudo ./gradlew --continuous`.

For continuous integration and development without Docker or the project wrapper
use Gradle directly. This will create the wrapper in case it is not present.
Similar to the above, for a CI cycle use `sudo gradle --continuous`. Gradle
3.4.1 is required for this to work. Plain Docker is also available for remote
integration tasks and alike. Build the image with `sudo docker build .` and run
a new container with it. Information on how to install Docker and docker-compose
can be found in their [official page][install-docker-compose]. A similar
installation guide is available [for Gradle][install-gradle].

## Troubleshooting

The [issue tracker][issue-tracker] intends to manage and compile bugs,
enhancements, proposals and tasks. Reading through its material or reporting to
its contributors via the platform is strongly recommended.

## Contributing

This project adheres to [Semantic Versioning][semver] and to certain syntax
conventions defined in [.editorconfig][editorconfig]. To get a list of changes
refer to the [CHANGELOG][changelog]. Only branches prefixed by *feature-*,
*hotfix-*, or *release-* will be considered:

  - Fork the project.
  - Create your new branch: `git checkout -b feature-my-feature develop`
  - Commit your changes: `git commit -am 'Added my new feature.'`
  - Push the branch: `git push origin feature-my-feature`
  - Submit a pull request.

## Credits

This project is created by [mbp76][author] and maintained by its
[author][author] and contributors.

## License

This project is licensed under the [Apache License Version 2.0][license].

[author]: https://mbp76.github.io
[issue-tracker]: https://github.com/mbp76/django-endpoint/issues
[editorconfig]: .editorconfig
[changelog]: CHANGELOG.md
[license]: LICENSE
[semver]: http://semver.org
[install-docker-compose]: https://docs.docker.com/compose/install/
[install-gradle]: https://gradle.org/install
