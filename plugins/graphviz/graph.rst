=====source_to_sor=====



<graphviz dot svg>

digraph "source_to_sor"{

    "Source = File or DB-Table?" [shape="diamond"];

    source_to_sor [shape="box" style="rounded" color="blue" width=3
                    URL="https://wiki.nlhcbi.com/doku.php?id=cbi:engineering:pyelt_proces:source_to_sor_details" target="_parent"];

    source_to_sor_by_hash [shape="box" style="rounded" color="blue" width=3
                    URL="https://wiki.nlhcbi.com/doku.php?id=cbi:engineering:pyelt_proces:source_to_sor_by_hash" target="_parent"];

    # proces diagram:
    start -> "Source = File or DB-Table?"
    "Source = File or DB-Table?" -> source_to_sor [label=" Source-file"]
    "Source = File or DB-Table?" -> source_to_sor_by_hash [label=" DB-table"]

    source_to_sor -> end;
    source_to_sor_by_hash -> end;

}
</graphviz>

Terug naar: [[cbi:engineering:pyelt_proces:pipe.run(parts)]]

return -> _get_fixed_params
_get_fixed_params -> "mappings.get_fields1"
"mappings.get_fields1" -> "mappings.get_keys"

"mappings.get_keys" -> "mappings get fields2"
"mappings get fields2" -> "mappings.get_fields_compare"

"mappings.get_fields_compare" -> "mappings.get_keys_compare"
"mappings.get_keys_compare" -> "mappings.get_source_encoding"
"mappings.get_source_encoding" -> "mappings.source.to_csv"
"mappings.source.to_csv" -> "sql: truncate temp_table"
"sql: truncate temp_table" -> "sql: copy into temp_table"
"sql: copy into temp_table" -> "sql: insert new into sor_table"
"sql: insert new into sor_table" -> "sql: update revision"
"sql: update revision" -> "sql: update set old ones inactive"
"sql: update set old ones inactive" -> end







[[cbi:engineering:pyelt_proces:source_to_sor_by_hash]]\\
[[cbi:engineering:pyelt_proces:_get_fixed_params]]\\
[[cbi:engineering:pyelt_proces:mappings.get_fields]]\\
[[cbi:engineering:pyelt_proces:mappings.get_keys]]\\
[[cbi:engineering:pyelt_proces:mappings.get_fields_compare]]\\
[[cbi:engineering:pyelt_proces:mappings.get_keys_compare]]\\
[[cbi:engineering:pyelt_proces:mappings.get_source_encoding]]\\
[[cbi:engineering:pyelt_proces:mappings.source.to_csv]]\\

Terug naar: [[cbi:engineering:pyelt_proces:pipe.run(parts)]]\\




<graphviz dot svg>

digraph "source_to_sor"{

subgraph cluster_1 {
                "sql: truncate temp_table"
		"sql: copy into temp_table"
		"sql: insert new into sor_table"
		"sql: update revision"
                "sql: update set old ones inactive"

                node [shape="box" style="rounded" color="blue"];
		"_get_fixed_params"

		"mappings.get_keys"

		"mappings.get_fields_compare"
		"mappings.get_keys_compare"
		"mappings.get_source_encoding"
                 "mappings.source.to_csv"


                node [shape="box" style="rounded" color="blue" label="mappings.get_fields"];
                "mappings.get_fields1"
                "mappings get fields2"



		label = "try" labeljust="l"

	}





# special format of box:

source_to_sor_by_hash[shape="box" style="rounded" color="blue"];



    #   comment box:

    #"(alias)='tmp'" [shape = plaintext]
    #{rank=same; "mappings get fields2";"(alias)='tmp'"}


    # proces diagram:
    start -> "Source = File or DB-Table?"
    "Source = File or DB-Table?" -> source_to_sor [label=" file"]
    "Source = File or DB-Table?" -> source_to_sor_by_hash [label=" DB-table"]

    source_to_sor -> end;
    source_to_sor_by_hash -> end;

}
</graphviz>

return -> _get_fixed_params
_get_fixed_params -> "mappings.get_fields1"
"mappings.get_fields1" -> "mappings.get_keys"

"mappings.get_keys" -> "mappings get fields2"
"mappings get fields2" -> "mappings.get_fields_compare"

"mappings.get_fields_compare" -> "mappings.get_keys_compare"
"mappings.get_keys_compare" -> "mappings.get_source_encoding"
"mappings.get_source_encoding" -> "mappings.source.to_csv"
"mappings.source.to_csv" -> "sql: truncate temp_table"
"sql: truncate temp_table" -> "sql: copy into temp_table"
"sql: copy into temp_table" -> "sql: insert new into sor_table"
"sql: insert new into sor_table" -> "sql: update revision"
"sql: update revision" -> "sql: update set old ones inactive"
"sql: update set old ones inactive" -> end







[[cbi:engineering:pyelt_proces:source_to_sor_by_hash]]\\
[[cbi:engineering:pyelt_proces:_get_fixed_params]]\\
[[cbi:engineering:pyelt_proces:mappings.get_fields]]\\
[[cbi:engineering:pyelt_proces:mappings.get_keys]]\\
[[cbi:engineering:pyelt_proces:mappings.get_fields_compare]]\\
[[cbi:engineering:pyelt_proces:mappings.get_keys_compare]]\\
[[cbi:engineering:pyelt_proces:mappings.get_source_encoding]]\\
[[cbi:engineering:pyelt_proces:mappings.source.to_csv]]\\

Terug naar: [[cbi:engineering:pyelt_proces:pipe.run(parts)]]\\

