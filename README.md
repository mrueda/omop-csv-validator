# Links

**📦 CPAN Distribution:** <a href="https://metacpan.org/pod/OMOP::CSV::Validator" target="_blank">https://metacpan.org/pod/OMOP::CSV::Validator</a>

# OMOP CSV Validator

The OMOP CSV Validator is a **CLI tool** (and module) that **validates OMOP CDM CSV files against their expected data types**. Rather than relying solely on `Types::Standard` or similar libraries, it converts SQL schemas derived from the OMOP Common Data Model (CDM) PostgreSQL DDL files into JSON schemas. It then utilizes `JSON::Validator`, which **scales efficiently with large datasets and provides meaningful error messages**.

## Features

- **DDL Parsing:** Automatically converts PostgreSQL OMOP CDM DDL into JSON schemas.
- **Version Independent** Works with any DDL (e.g., 5.3, 5.4).
- **CSV Validation:** Validates CSV files using JSON::Validator.
- **Modular Design:** Separate CLI and module for easy testing and integration.

## Installation

This project uses [cpanm](https://metacpan.org/pod/App::cpanminus) along with a `cpanfile` to manage dependencies. It is recommended to install dependencies locally using `local::lib`.

### Step 1: Install cpanminus

If you don't have `cpanm` installed, run:

```bash
sudo apt-get install cpanminus
```

If you don't have `gcc` compiler and other default Linux utils installed please do:

```bash
sudo apt-get install gcc make libperl-dev
```

### Step 2: Set Up local::lib

Configure a local library in your home directory. For example:

```bash
cpanm --local-lib=~/perl5 local::lib && eval $(perl -I ~/perl5/lib/perl5/ -Mlocal::lib)
```

Then, add this settings to your shell profile (e.g. `~/.bashrc` or `~/.zshrc`) so that your shell knows about your local library.

```bash
echo 'eval $(perl -I ~/perl5/lib/perl5/ -Mlocal::lib)' >> ~/.bashrc
```

### Step 3: Download and installation:

#### From CPAN

```bash
cpanm OMOP::CSV::Validator --no-test
```

#### From Github

1. Clone the repository:

```bash
git clone https://github.com/mrueda/omop-csv-validator.git
cd omop-csv-validator
```

2. Install Dependencies:

```bash
cpanm --notest --installdeps .
```

This command reads the included `cpanfile` and installs all required dependencies into your local library directory.

## Usage

### Command-Line Interface

Once dependencies are installed, you can run the CLI tool as follows:

(If you installed fron CPAN then you can simply run `omop-csv-validator`).

```bash
bin/omop-csv-validator --ddl path/to/OMOPCDM_ddl.sql --input path/to/data.csv --sep ","
```

With the included `example` data:

```bash
bin/omop-csv-validator --ddl ddl/OMOPCDM_postgresql_5.4_ddl.sql -i example/DRUG_EXPOSURE.csv -sep $'\t'
```

## Running Tests

To run the test suite, execute:

```bash
prove -l t/
```

## Utilities

* `reorder-csv.pl`

See directory [utils](utils/README.md).

## Author 

Written by Manuel Rueda, PhD. Info about CNAG can be found at [https://www.cnag.eu](https://www.cnag.eu).

## Contributing

Contributions, issues, and feature requests are welcome. Please check the [issues](https://github.com/yourusername/yourrepo/issues) page for details.

## License

This project is released under the [Artistic License 2.0](LICENSE).
