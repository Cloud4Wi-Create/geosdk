# Configurations and Selection Operators

This section lists the various [Geometries](/api/concepts/resource-definition.md#geometries) defined by this API as well as the set of [Dimensional Selection Operators](/api/concepts/resource-selection.md#dimensional-selection-operation) that are allowed for each of them

# Configurations

The following set of Geometries are defined.

- ***Point***. The Resource assumes a single value on the Dimension.
- ***Multipoint***. The Resource is defined as a set of *Points* not related to each other.
- ***Sequence***. The Resource is defined as a set of *Points* ordered according to a criterion. The first *Point* is said **Start Point**, whilst the last is said **End Point**.
- ***Interval***. Exists only for those Dimensions whose space of values can be ordered. The Resource is defined as a Sequence: a) whose *Points* follow same sorting as the specific Dimension; b) that contains all the possible Points between the Start Point and the End Point.

<a name="operators"></a>
# Selection Operators

The following set of Dimensional Selection Operators are defined.

* ***inside***.
    * Inidcated as: `"inside"`.
    * Allowed For: *Point*; *Multipoint*; *Sequence*; *Interval*.
    * All the values assumed by the Resource on the Dimension must be inside a specific *D* Segment.
* ***intersect***.
    * Inidcated as: `"intersect"`.   
    * Allowed For: *Multipoint*; *Sequence*; *Interval*.    
    * At least one the values assumed by the Resource on the Dimension must be inside a specific *D* Segment.
* ***start***.
    * Inidcated as: `"start"`   .
    * Allowed For: *Sequence*; *Interval*.    
    * The Start Point assumed by the Resource on the Dimension must be inside a specific *D* Segment.
* ***end***.
    * Inidcated as: `"end"`  . 
    * Allowed For: *Sequence*; *Interval*.    
    * The End Point assumed by the Resource on the Dimension must be inside a specific *D* Segment.
