# Migration guides

## From v9 to v10

1. New dynamic values support.
   In v9, observables and function values have been part of JSS core. In v10 they are standalone plugins. If you are using the default preset you don't need to do anything else than upgrading the default preset and JSS. If you are using a custom setup and you use function values or observables, you will have to add 2 additional plugins. See [plugins.md](./plugins.md).

1. Full syntax support in dynamic values.
   Return values from observables and functions are now processed by the JSS plugins. This means you can return full JSS syntax from dynamic values. This also means it can be a bit slower, but you can opt-out from processing by using `sheet.update(data, {process: false})` when using JSS core directly. Also you can opt-out when setting up the observable plugin `jss.use(pluginObservable({process: false}))`.

1. Scoped @keyframes.
   In v9, when you declare keyframes `@keyframes my-animation` the `my-animation` ID was global, as it is by default in CSS. This could lead to problems since you could override them nondeterministically. In v10, ID is scoped by default, same as we do with class names. Check out the full syntax [here](./jss-syntax.md/#keyframes-animation).

1. Renamed ID generator function.
   Due to the fact, that we now use the same ID generator function for both class names and keyframes ID, we had to rename functions `createGenerateClassName` and `generateClassName` to `createGenerateId` and `generateId`.

1. Dropping support for React 0.13, 0.14 and 0.15.
   React-JSS has migrated to the new Context API and now requires React v16 or higher.