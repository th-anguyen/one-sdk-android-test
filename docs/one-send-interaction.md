[Thunderhead](../index.md) / [com.thunderhead.android.api](index.md) / [oneSendInteraction](./one-send-interaction.md)

# oneSendInteraction

`suspend fun oneSendInteraction(throwErrors: `[`Boolean`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html)` = false, initializer: Builder.() -> `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)`): `[`OneResponse`](../com.thunderhead.android.api.responsetypes/-one-response/index.md)`?`

Send interaction to the Thunderhead API.

### Parameters

`initializer` - [OneRequest.Builder](../com.thunderhead.android.api.interactions/-one-request/-builder/index.md) initializer to create a [OneRequest](../com.thunderhead.android.api.interactions/-one-request/index.md).

`throwErrors` - [Boolean](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html) true to enable throwable errors. When enabled, wrap this method in a `try/catch` block.

**Return**
response [OneResponse](../com.thunderhead.android.api.responsetypes/-one-response/index.md) result of request

