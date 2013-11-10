grails-foundation4-resources-plugin
===================================

Grails plugin for Zurb Foundation 4 (http://foundation.zurb.com/).

Current version is 4.3.2.1, the numbering is based on Foundation release numbering, plus plugin version number: <4.3.2>.<1>, where 4.3.2 is the current Foundation release version.

Simple usage
------------

Use the defined resource in the GSP file:

    <r:require module="foundation" />

and all the necessary Foundation files will be added to the generated resource bundle.

Usage with own CSS files
------------------------

If you want to use your own generated CSS files (both from the Foundation page or your own generated by Compass), you can still reuse the defined resource modules. You just define you own top level module using the existing one, plus your CSS file in the ApplicationResources:

    'my-foundation-css' {
        resource url: 'css/custom.css' // this is your own generated CSS file
    }

    'my-foundation' {
        dependsOn 'foundation-modules', 'my-foundation-css' // the 'foundation-modules' contains all the Foundation plugins, plus the dependency on Foundation core JS files
    }

and in the GSP file just use:

    <r:require module="my-foundation" />

and you have your own CSS files instead of the default one.

Fully own build
---------------

You can also reuse the definition of the Foundation modules, each has it's own resource module, so you can combine them as you want.

    'my-foundation-css' {
        resource url: 'css/custom.css' // this is your own generated CSS file
    }

    'my-foundation-modules' {
        dependsOn 'foundation-dropdown', 'foundation-forms' // own set of Foundation modules
    }

    'my-foundation-build' {
        dependsOn 'my-foundation-modules', 'my-foundation-css'
    }

In the GSP use it as usual:

    <r:require module="my-foundation-build" />

