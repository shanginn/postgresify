# Laravel Postgresify

## Table of Contents


**[What is this?](#what-is-this)**


**[Installation?](#installation)**


**[Geometric Types](#geometric-types)**

* [Box](#box)
* [Circle](#circle)
* [Line](#line)
* [Line Segment](#line-segment)
* [Path](#path)
* [Point](#point)
* [Polygon](#polygon)


**[Monetary Types](#monetary-types)**

* [Money](#money)


**[Network Address Types](#network-address-types)**

* [IP Address](#ip-address)
* [MAC Address](#mac-address)
* [Netmask](#netmask)


**[Range Types](#range-types)**

* [Date Range](#date-range)
* [Integer Range](#integer-range)
* [Numeric Range](#numeric-range)
* [Timestamp Range](#timestamp-range)
* [Timestamp Range w/ Timezone](#timestamp-timezone-range)


**[License](#license)**

**[References](#references)**

## What is this?
Laravel Postgresify, just Postgresify for short, is a package for Laravel and Lumen that extends support to some of the
more useful PostgreSQL data types. This package allows you to leverage PostgreSQL's data types, such as point, inet,
circle, etc., within Laravel's Schema Builder and retrieve meaningful data from Fluent/Eloquent.

Example Migration:
```php
Schema::create('hotel_search', function (Blueprint $table) {
    ...

    $table->point('geocode_coordinates');
    $table->ipAddress('visitor_ip_address');
    $table->circle('search_area');
    $table->dateRange('reservation_period');
    $table->money('budget');

    ...
});
```

Life's easier, right? The above use cases of PostgreSQL's types eliminate a few immediately noticeable headaches:
- Point types store geographic coordinates in one field--not two. This may ease query writing, more on that in a second.
- IP address types will store IPv4 or IPv6--no `VARCHAR` here.
- Circle types store a center point and a radius <(x, y), r>. I've seen hacky ways to store radii without this.
- Date range types store just that, date ranges. This, like the point type, eliminates the necessity of the second field.
- Money types store a signed, locale-sensitive currency amount, with a range of +/- 92 quadrillion! No more `DECIMAL(11,2)` or whatever people do these days.

Now let's discuss the actual utility afforded by these additional types. PostgreSQL is nicely equipped with functions
and operators for meaningfully working with these data types. This depends on the architecture of your environment, but
these types combined with the functions/operators allow you to offload some work onto your database server--which might
be faster and could reduce some responsibilities within your application's code. Your mileage may vary. See this
[StackExchange Q/A](http://programmers.stackexchange.com/questions/171024/never-do-in-code-what-you-can-get-the-sql-server-to-do-well-for-you-is-this).

## Geometric Types

### Box

### Circle

### Line

### Line Segment

### Path

### Point

### Polygon


## Monetary Types

### Money


## Network Address Types

### IP Address

### MAC Address

### Netmask


## Range Types

### Date Range

### Integer Range

### Numeric Range

### Timestamp Range

### Timestamp Range w/ Timezone


## License

- [MIT](https://raw.githubusercontent.com/aejnsn/laravel-postgresify/master/LICENSE).

## References

- [PostgreSQL 9.4 Manual](http://www.postgresql.org/docs/9.4/static/datatype.html).