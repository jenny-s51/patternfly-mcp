# Component Schemas Tool

The `component-schemas` tool provides access to PatternFly component JSON schemas for validation and documentation purposes. This tool integrates the [@patternfly/patternfly-component-schemas](https://github.com/patternfly/patternfly-component-schemas) package to give you structured metadata about all PatternFly React components.

## Features

- **List all components**: Get a complete list of all 462+ PatternFly components
- **Get component schema**: Retrieve detailed JSON Schema for any specific component
- **Prop validation**: Access structured validation rules for component props
- **Type information**: Get prop types, required fields, and enum values
- **AI-friendly**: Designed for AI assistants and code generation tools

## Usage

### List All Components

```json
{
  "action": "list"
}
```

**Response:**
```json
{
  "action": "list",
  "totalComponents": 462,
  "components": ["AboutModal", "Alert", "Button", "Card", ...],
  "description": "Available PatternFly React components with JSON Schema validation"
}
```

### Get Component Schema

```json
{
  "action": "get",
  "componentName": "Button"
}
```

**Response:**
```json
{
  "action": "get",
  "componentName": "Button",
  "propsCount": 24,
  "requiredProps": [],
  "schema": {
    "type": "object",
    "properties": {
      "variant": {
        "type": "string",
        "enum": ["primary", "secondary", "tertiary", "danger", "warning", "link", "plain", "control"]
      },
      "size": {
        "type": "string", 
        "enum": ["sm", "md", "lg"]
      },
      "children": {
        "type": "string"
      },
      "isDisabled": {
        "type": "boolean"
      }
      // ... more properties
    }
  },
  "description": "JSON Schema for Button component props"
}
```

## Error Handling

### Component Not Found

If you request a component that doesn't exist, the tool provides helpful suggestions:

```json
{
  "action": "get",
  "componentName": "InvalidComponent"
}
```

**Response:**
```json
{
  "error": "Component \"InvalidComponent\" not found",
  "availableComponents": ["Button", "Card", "Modal"],
  "suggestion": "Use the \"list\" action to see all available components"
}
```

### Missing Component Name

```json
{
  "action": "get"
}
```

**Response:**
```json
{
  "error": "componentName is required when action is \"get\"",
  "usage": {
    "listComponents": { "action": "list" },
    "getComponentSchema": { "action": "get", "componentName": "Button" }
  }
}
```

## Use Cases

### AI Code Generation

AI assistants can use this tool to:
- Discover available PatternFly components
- Validate generated component props
- Understand component structure and requirements
- Generate type-safe React code

### Component Discovery

```json
{
  "action": "list"
}
```

Use the list action to explore all available components and find the right one for your needs.

### Prop Validation

```json
{
  "action": "get",
  "componentName": "Alert"
}
```

Get the complete schema to understand:
- Required vs optional props
- Prop types (string, boolean, enum, etc.)
- Valid enum values
- Component structure

### Form Builders

The schemas can be used to build dynamic forms or component configurators that ensure valid prop combinations.

## Available Components

The tool provides access to all PatternFly React components including:

- **Data Display**: Table, List, Card, DataList, DescriptionList
- **Forms**: FormGroup, TextInput, Select, Checkbox, Radio
- **Navigation**: Nav, Breadcrumb, Tabs, Pagination, Wizard
- **Feedback**: Alert, Modal, Popover, Tooltip, Banner
- **Layout**: Page, Sidebar, Toolbar, Bullseye, Grid
- **Actions**: Button, Dropdown, MenuToggle, ActionList
- **Charts**: All PatternFly chart components
- **And many more...**

## Integration with Other Tools

The component schemas tool works well with other PatternFly MCP tools:

1. **Use with `patternfly-docs`**: Get documentation and examples
2. **Use with `fetch-docs`**: Get detailed component guides
3. **Combine schemas with examples**: Validate generated code against real examples

## Technical Details

- **Package**: `@patternfly/patternfly-component-schemas`
- **Schema Format**: JSON Schema Draft 2020-12
- **Component Count**: 462+ components
- **Prop Count**: 3,487+ component props
- **Runtime Validation**: Supports Zod schemas for runtime validation

## Example Workflow

1. **Discover components**:
   ```json
   { "action": "list" }
   ```

2. **Get component details**:
   ```json
   { "action": "get", "componentName": "Button" }
   ```

3. **Use schema for validation**:
   - Check required props
   - Validate prop types
   - Ensure enum values are correct

4. **Generate type-safe code**:
   - Use schema to generate TypeScript interfaces
   - Create component instances with validated props
   - Build forms or configurators

This tool is essential for AI-assisted development, providing the structured metadata needed to generate correct and type-safe PatternFly component usage.
