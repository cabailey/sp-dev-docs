---
title: Fields element (WorkflowConfig)
description: Describes the definition, element, and attribute information for the Fields element (WorkflowConfig).
manager: laurawi
ms.date: 06/09/2022
ms.audience: Developer
ms.topic: reference
f1_keywords:
- SharePoint Workflows
ms.prod: sharepoint
ms.localizationpriority: medium
ms.assetid: 6b49e059-250e-4b9f-b32e-72ca5fe150c9
---

# Fields element (WorkflowConfig)

**Applies to**: SharePoint 2016 | SharePoint Foundation 2013 | SharePoint Online | SharePoint Server 2013

Represents a collection of the data fields included on the workflow initiation form.

## Definition

```XML
<Fields>
</Fields>
```

## Elements and attributes

The following sections describe attributes, child elements, and parent elements.

|Attributes|
|----------|
|None.|

|Child elements|
|--------------|
|[Field Element (Field)](field-element-field.md) (see Remarks)|

|Parent elements|
|---------------|
|[Initiation Element (WorkflowConfig)](initiation-element-workflowconfig.md)|

### Remarks

The **Fields** element contains a collection of [Field Element (Field)](field-element-field.md) elements. Each [Field Element (Field)](field-element-field.md) element represents a data field on the workflow initiation form.

To specify a default value for a field, add a **Default** element to the [Field Element (Field)](field-element-field.md) element.

For each [Field Element (Field)](field-element-field.md) element contained in the **Fields** element, there must be a corresponding [Parameter Element (WorkflowConfig)](parameter-element-workflowconfig.md) element with a matching Name attribute. The [Parameter Element (WorkflowConfig)](parameter-element-workflowconfig.md) element specifies the System data type of the field.

The [Parameter Element (WorkflowConfig)](parameter-element-workflowconfig.md) element also represents a workflow variable of the same name. When the user submits the workflow initiation form, SharePoint Foundation passes the value specified for each parameter to the workflow instance as part of the [InitiationData](https://msdn.microsoft.com/library/office/microsoft.sharepoint.workflow.spworkflowactivationproperties.initiationdata.aspx) property.

Use the URL attribute of the [Initiation Element (WorkflowConfig)](initiation-element-workflowconfig.md) element to specify the path to the workflow initiation form for the workflow.

## Example

The following example Initiation element contains a URL attribute that specifies the location of the workflow initiation form to use for this workflow.

The element also contains a Fields element, which in turn contains a Field element that defines the single data field on the initiation form. Note that the [Parameters Element (WorkflowConfig)](parameters-element-workflowconfig.md) element contains a corresponding [Parameter Element (WorkflowConfig)](parameter-element-workflowconfig.md) element, with a matching Name attribute value that specifies the data type of the Field element.

This example has been edited for clarity.

```XML
    <Initiation 
        URL="Workflows/Notify Me/Notify Me.aspx">
      <Fields>
        <Field 
          Name="Reason_for_Review" 
          …
          DisplayName="Reason for Review" 
          …
        >
          <Default>Standard review of new documents</Default>
        </Field>
      </Fields>
      <Parameters>
        <Parameter Name="Reason_for_Review" Type="System.String" />
      </Parameters>
    </Initiation>
```

## See also

- [Workflow configuration schema reference](workflow-configuration-schema-reference.md)
- [Workflow Development for Windows SharePoint Services](https://msdn.microsoft.com/library/office/ms414613.aspx)
- [Creating Declarative, No-Code Workflow Editors](https://msdn.microsoft.com/library/office/bb417436.aspx)
- [Office SharePoint Designer Overview](https://msdn.microsoft.com/library/office/ms454098.aspx)





