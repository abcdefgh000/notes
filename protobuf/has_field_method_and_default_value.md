A string field (like `name`) inside a protobuf message has a default value of "", if the user does not set its value, then it will be empty string.

The method `.has_name()` will return `true` if the user has set the field, and `false` if the field only has the default value.
