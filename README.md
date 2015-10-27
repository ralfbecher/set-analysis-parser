# set-analysis-parser

> Parse for Set Analaysis expressions in Qlik's products..

<!-- toc -->

* [About this project](#about-this-project)
* [Install](#install)
* [Contributing](#contributing)
* [Author](#author)
* [License](#license)
* [Related projects](#related-projects)

_(Table of contents generated by [verb])_

<!-- tocstop -->

> **This is work in progress, read below.**

## About this project

The backbone of the new Set Analysis Wizard will be a parser which is able to parse and therefore "decode" existing Set Analysis statements into a structure whic can be used in programmatic way.

**The Parser**

I have chosen to use [Jison](http://zaach.github.io/jison/) to parse existing Set Analysis statements.

If you have a look into the online documentation of Qlik Sense, you'll find the [BNF](https://en.wikipedia.org/wiki/Backus%E2%80%93Naur_Form) syntax for sets there:

```
// Added entry point
definition ::= aggr_type ( set_expression field_expression )

// From the online help
// http://help.qlik.com/sense/2.0/en-US/online/Subsystems/Hub/Content/ChartFunctions/SetAnalysis/syntax-for-sets.htm
set_expression ::= { set_entity { set_operator set_entity } }
set_entity ::= set_identifier [ set_modifier ]
set_identifier ::= 1 | $ | $N | $_N | bookmark_id | bookmark_name
set_operator ::= + | - | * | /
set_modifier ::= < field_selection {, field_selection } >
field_selection ::= field_name [ = | += | ¬–= | *= | /= ] element_set_expression
element_set_expression ::= element_set { set_operator element_set }
element_set ::= [ field_name ] | { element_list } | element_function
element_list ::= element { , element }
element_function ::= ( P | E ) ( [ set_expression ] [ field_name ] )
element ::= field_value | " search_mask "
```

**Semantic sugar layer**

The goal is that you can paste in the following expression

```
Sum({$<Customer=P({1<Product={'Shoe'}>}Customer)>}Sales)
```

and you'll get back the following description

> Returns the Sum of Sales for the current selection, but only for those customers that have bought the product "Shoe".

This semantic explanation of a Set Analysis wizard can then either be used just to "decode" an existing statement or used in a tool like the Set Analysis Wizard.

## Install

## Contributing

Pull requests and stars are always welcome. For bugs and feature requests, [please create an issue](https://github.com/stefanwalther/set-analysis-parser/issues/new).

## Author

**Stefan Walther**

+ [qliksite.io](http://qliksite.io)
* [twitter/waltherstefan](http://twitter.com/waltherstefan)
* [github.com/stefanwalther](http://github.com/stefanwalther)

## License

Copyright © 2015 Stefan Walther
Released under the GNU General Public License license.

## Related projects

Some related projects (Qlik Sense Visualization Extensions) I have recently created:

[set-analysis-wizard](https://www.npmjs.com/package/set-analysis-wizard): The well known Set Analysis Wizard for QlikView and Qlik Sense. | [homepage](https://github.com/stefanwalther/set-analysis-wizard)

***

_This file was generated by [verb-cli](https://github.com/assemble/verb-cli) on October 27, 2015._