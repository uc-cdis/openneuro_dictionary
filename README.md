Data Model for Open Access Data

# Data Dictionary

The data dictionary provides the first level of validation for all submitted data.
Written in YAML, JSON schemas define all the individual entities
(nodes) in the data model. Moreover, these schemas define all of the relationships (links)
between the nodes. Finally, the schemas define the valid key-value pairs that can be used to
describe the nodes.

## Data Dictionary Structure

The Data Model covers all of the nodes within the as well as the relationships between
the different types of nodes. All of the nodes in the data model are strongly typed and individually
defined for a specific data type. Doing such allows for faster querying of
the data model as well as providing a clear and concise representation of the data.

Beyond node type, there are also a number of extensions used to further define the nodes within
the data model. Nodes are grouped up into categories that represent broad roles for the node such
as `analysis` or `biospecimen`. Additionally, nodes are defined within their `Program` or `Project`
and have descriptions of their use. All nodes also have a series of `systemProperties`; these
properties are those that will be automatically filled by the system unless otherwise defined by
the user.  These basic properties define the node itself but still need to be placed into the model.

The model itself is represented as a graph. Within the schema are defined `links`; these links
point from child to parent with Program being the root of the graph. The links also contain a
`backref` that allows for a parent to point back to a child. Other features of the link include a
semantic `label` that describes the relationship between the two nodes, a `multiplicity` property
that describes the numeric relationship from the child to the parent, and a requirement property
to define whether a node must have that link. Taken all together the nodes and links create the
directed graph of the Data Model.

## Node Properties and Examples

Each node contains a series of potential key-value pairs (`properties`) that can be used to
characterize the data they represent. Some properties are categorized as `required` or `preferred`.
If a submission lacks a required property, it cannot be accepted. Preferred properties can denote
two things: the property is being highlighted as it has become more desired by the community or
the property is being promoted to required. All properties not designated either `required` or
`preferred` are still sought by BPA, but submissions without them are allowed.

The properties have further validation through their entries. Legal values are defined in each
property. For the most part these are represented in the `enum` categories although some keys,
such as `submitter_id`, will allow any string value as a valid entry. Other numeric properties
can have maximum and minimum values to limit valid entries.  For examples of what a valid entry
would look like, each node has a mock submission located in the `examples/valid/` directory.
