In order to demonstrate the issue with sharing the error bag context using shared components create a build preview of this site,

`npm i` inside both apps,

in the main app
`npm run build && npm run preview`

this simulates a production build (which is the only place this issue occurs!)

As you can see the errors in the shared component do not work. This applies to components that come from both nuxt-layers and nuxt-modules.
We are trying to create shared form components that we use across multiple apps and this issue has been workedaround by duplicating multiple versions of our label input wrapper which displays our errors.
This is also true of useForm useField and useFieldError implementations, 
they all work fine when running the project locally.
