# FormValidation

The `FormValidation` class configures the **error messages** returned by a service external to the application. For example, when checking the registration status of a CPF in the recipe, we can return the **API error message to the application** using `FormValidation`. This is your structure:

```kotlin
data class FormValidation(
    val errors: List<FieldError>
) : Action
```

### errors

List of errors that API validation can return.

```kotlin
data class FieldError(
    val inputName: String,
    val message: String
)
```

#### inputName

Name of the `FormInput` component to which **this error refers**.

#### message

**Error message** to be displayed.

