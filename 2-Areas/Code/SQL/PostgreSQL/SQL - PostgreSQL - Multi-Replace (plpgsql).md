# SQL - PostgreSQL - Multi-Replace (plpgsql)

*Source: https://wiki.postgresql.org/wiki/Multi_Replace_plpgsql*

*NOTE: This function is generic [SQL](../../../../3-Resources/Tools/Developer%20Tools/Data%20Stack/Procedural%20Languages/SQL.md):*

````SQL
/* This function quotes characters that may be interpreted as special in a regular expression.
   It's used by the function below and declared separately for clarity. */
CREATE FUNCTION quote_meta(text) RETURNS text AS $$
  select regexp_replace($1, '([\[\]\\\^\$\.\|\?\*\+\(\)])', '\\\1', 'g');
$$ language sql strict immutable;
````

*NOTE: This function uses the [PLPGSQL](../../../../3-Resources/Tools/Developer%20Tools/Data%20Stack/Procedural%20Languages/PLPGSQL.md) language.*

````SQL
/* Substitute a set of substrings within a larger string.
   When several strings match, the longest wins.
   Similar to php's strtr(string $str, array $replace_pairs).
   Example:
   select multi_replace('foo and bar is not foobar',
             '{"bar":"foo", "foo":"bar", "foobar":"foobar"}'::jsonb);
   => 'bar and foo is not foobar'
 */
CREATE FUNCTION multi_replace(str text, substitutions jsonb)
RETURNS text
as $$
DECLARE
 rx text;
 s_left text;
 s_tail text;
 res text:='';
BEGIN
 select string_agg(quote_meta(term), '|' )
 from jsonb_object_keys(substitutions) as x(term)
   where term <> ''
 into rx;

 if (coalesce(rx, '') = '') then
   -- the loop on the RE can't work with an empty alternation
   return str;
 end if;

 rx := concat('^(.*?)(', rx, ')(.*)$'); -- match no more than 1 row   

 loop
   s_tail := str;
   select 
       concat(matches[1], substitutions->>matches[2]),
       matches[3]
    from
      regexp_matches(str, rx, 'g') as matches
    into s_left, str;
    
   exit when s_left is null;
   res := res || s_left;

 end loop;

 res := res || s_tail;
 return res;

END 
$$ LANGUAGE plpgsql strict immutable;
````

---

## Appendix: Links

* *Code*
* [SQL](../../../../3-Resources/Tools/Developer%20Tools/Data%20Stack/Procedural%20Languages/SQL.md)
* [Databases](../../../MOCs/Databases.md)
* [PostgreSQL](../../../../3-Resources/Tools/Developer%20Tools/Data%20Stack/Databases/PostgreSQL.md)
* [PLPGSQL](../../../../3-Resources/Tools/Developer%20Tools/Data%20Stack/Procedural%20Languages/PLPGSQL.md)
* [Development](../../../MOCs/Development.md)

*Backlinks:*

````dataview
list from [[SQL - Multi-Replace (plpgsql)]] AND -"Changelog"
````
