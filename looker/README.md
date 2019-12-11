# Hey Ma! Look at my awesome LookML! Sideways!

Grand Rounds started using Looker and LookML *way* before there was a
Looker style guide (in fact, way before LookML stopped being just YAML),
so *most* of what you'll read in our existing LookML does *not* conform
to current best practice.

*However*, let's start there: For new LookML, unless
there are good reasons, please follow the [Look at me
Sideways](https://looker-open-source.github.io/look-at-me-sideways/rules.html)
conventions.

But there are some exceptions:
* Primary Key differences
* Time field differences

## Primary Keys

Redshift does not offer a way to ensure that primary keys are actually
unique -- after all, it has no notion of "index" that might be used to
implement such a feature. Compounding this problem, our event delivery
system (Kinesis), at least in our initial implementations, could only
offer "at least once" delivery in the face of errors.

For datasets (tables) that cannot guarantee the uniqueness of the
primary key, *do not declare a primary key*.  Looker will then generate
GROUP BY operations that, though slow, will at least de-duplicate the
underlying data.

## Time field names

Our time field conventions are inherited from Active Record. These conventions
should be true across *all* of our systems (including those well outside the
Ruby culture), and especially in Looker.

Time field names in views should always end in `_at`, as
in `deleted_at`, `created_at`, etc. This allows us to write downstream tools
(e.g., our Looker -> Athena adapter code) which can correctly distinguish time
fields from character fields.

In addition, the following field names should always have the same meaning:

* `created_at`: The time the data record was created in the system of record, with at least second and preferably microsecond or better precision, in UTC.
* `updated_at`: The most time any field of the data record was created in the system of record. UTC, highest precision available.
* `deleted_at`: The the data record was (soft) deleted in the system of record. Again: UTC, highest precision available.

# Linters

Now that Looker has linters, LookML repos *should* be configured to use them.
They have not yet.
