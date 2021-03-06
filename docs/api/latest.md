# API Docs - v1.1.0

## Store

### solr *<a target="_blank" href="https://wso2.github.io/siddhi/documentation/siddhi-4.0/#store">(Store)</a>*

<p style="word-wrap: break-word">Solr store implementation uses solr collections for underlying data storage. The events are converted to Solr documents when the events are inserted to solr store. Solr documents are converted to Events when the Solr documents are read from solr collections. This can only be used with the Solr cloud mode.</p>

<span id="syntax" class="md-typeset" style="display: block; font-weight: bold;">Syntax</span>
```
@Store(type="solr", collection="<STRING>", zookeper.url="<STRING>", shards="<INT>", replicas="<INT>", schema="<STRING>", commit.async="<BOOL>", base.config="<STRING>", merge.schema="<BOOL>")
@PrimaryKey("PRIMARY_KEY")
@Index("INDEX")
```

<span id="query-parameters" class="md-typeset" style="display: block; color: rgba(0, 0, 0, 0.54); font-size: 12.8px; font-weight: bold;">QUERY PARAMETERS</span>
<table>
    <tr>
        <th>Name</th>
        <th style="min-width: 20em">Description</th>
        <th>Default Value</th>
        <th>Possible Data Types</th>
        <th>Optional</th>
        <th>Dynamic</th>
    </tr>
    <tr>
        <td style="vertical-align: top">collection</td>
        <td style="vertical-align: top; word-wrap: break-word">The name of the solr collection.</td>
        <td style="vertical-align: top">SolrTable_Id</td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">Yes</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">zookeper.url</td>
        <td style="vertical-align: top; word-wrap: break-word">The zookeeper url of the solr cloud</td>
        <td style="vertical-align: top">localhost:9983</td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">Yes</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">shards</td>
        <td style="vertical-align: top; word-wrap: break-word">The number of shards of the solr collection</td>
        <td style="vertical-align: top">2</td>
        <td style="vertical-align: top">INT</td>
        <td style="vertical-align: top">Yes</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">replicas</td>
        <td style="vertical-align: top; word-wrap: break-word">The number of replicas of the solr collection.</td>
        <td style="vertical-align: top">1</td>
        <td style="vertical-align: top">INT</td>
        <td style="vertical-align: top">Yes</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">schema</td>
        <td style="vertical-align: top; word-wrap: break-word">The explicit solr collection schema definition.</td>
        <td style="vertical-align: top">SolrTable_Schema</td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">Yes</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">commit.async</td>
        <td style="vertical-align: top; word-wrap: break-word">The explicit solr collection schema definition.</td>
        <td style="vertical-align: top">true</td>
        <td style="vertical-align: top">BOOL</td>
        <td style="vertical-align: top">Yes</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">base.config</td>
        <td style="vertical-align: top; word-wrap: break-word">The basic configset used to create the collection specific configurations.</td>
        <td style="vertical-align: top">Solr_Base_Config</td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">Yes</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">merge.schema</td>
        <td style="vertical-align: top; word-wrap: break-word">The basic configset used to create the collection specific configurations.</td>
        <td style="vertical-align: top">true</td>
        <td style="vertical-align: top">BOOL</td>
        <td style="vertical-align: top">Yes</td>
        <td style="vertical-align: top">No</td>
    </tr>
</table>

<span id="examples" class="md-typeset" style="display: block; font-weight: bold;">Examples</span>
<span id="example-1" class="md-typeset" style="display: block; color: rgba(0, 0, 0, 0.54); font-size: 12.8px; font-weight: bold;">EXAMPLE 1</span>
```
@store(type='solr', zookeeper.url='localhost:9983', collection='TEST1', base.config='gettingstarted', shards='2', replicas='2', schema='time long stored, date string stored', commit.async='true')define table Footable(time long, date string);
```
<p style="word-wrap: break-word">Above example will create a solr collection which has two shards with two replicas which is named TEST1, using the basic config 'gettingstarted'. it will have two fields time and date. both fields will be indexed and stored in solr. all the inserts will be committed asynchronously from the solr server side</p>

