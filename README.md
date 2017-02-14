# DITA Metrics Report

Obtain different metrics from a DITA map.

Applying the XSLT stylesheets requires an XSLT 2.0 processor (Saxon 9).

The publishing is done in two stages:

  - The **report.xsl** XSLT stylesheet is applied on the main DITA Map. This produces a special XML document containing all the report data.
  - On the XML document produced in the first stage  you should apply the **report2XHTML.xsl** XSLT stylesheet which produces the HTML output.


## License

This project is licensed under MPL 2.0, see the [LICENSE](LICENSE) file for details.

