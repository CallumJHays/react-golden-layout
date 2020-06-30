# React Golden Layout

[![NPM version](https://img.shields.io/npm/v/golden-layout)](https://www.npmjs.com/package/golden-layout) [![License](https://img.shields.io/github/license/golden-layout/golden-layout)](https://img.shields.io/github/license/golden-layout/golden-layout)

<!-- [![NPM version](https://badge.fury.io/js/golden-layout.svg)](http://badge.fury.io/js/golden-layout) [![Build Status](https://travis-ci.org/deepstreamIO/golden-layout.svg?branch=master)](https://travis-ci.org/deepstreamIO/golden-layout) -->

<!-- ![Screenshot](https://cloud.githubusercontent.com/assets/512416/4584449/e6c154a0-4ffa-11e4-81a8-a7e5f8689dc5.PNG) -->

Original project credit goes to: https://github.com/golden-layout/golden-layout.

## Overview
This project was forked from the original golden layout project, which unfortunately appears to have been abandoned. This is a forked & updated version of that original project to add compatability with React. This updated version now exports a `GoldenLayoutComponent` for easy integration into a React project.

Example usage:
```typescript
import React from 'react';
import '@annotationhub/golden-layout/dist/css/goldenlayout-base.css';
import '@annotationhub/golden-layout/dist/css/themes/goldenlayout-dark-theme.css';
import { GoldenLayoutComponent } from '@annotationhub/react-golden-layout';

function ComponentA() {
  return <h2>A</h2>;
}

function ComponentB() {
  return <h2>B</h2>;
}

function ComponentC() {
  return <h2>C</h2>;
}

export default function GoldenTest() {
  return (
    <div>
      <GoldenLayoutComponent
        htmlAttrs={{ style: { height: "100vh", width: "100vw" } }}
        config={{
          content: [{
            type: 'row',
            content:[{
              type:'react-component',
              component: 'ComponentA',
              title: 'A Component',
              props: { label: 'A' }
            }, {
              type: 'column',
              content:[{
                  type:'react-component',
                  component: 'ComponentB',
                  title: 'B Component',
                  props: { label: 'B' }
              },{
                  type:'react-component',
                  component: 'ComponentC',
                  title: 'C Component',
                  props: { label: 'C' }
              }]
            }]
          }]
        }}
        registerComponents={glLayout => {
          glLayout.registerComponent('ComponentA', ComponentA);
          glLayout.registerComponent('ComponentB', ComponentB)
          glLayout.registerComponent('ComponentC', ComponentC)
        }}
      />
    </div>
  );
}
```

## Features

* Full touch support
* Native popup windows
* Completely themeable
* Comprehensive API
* Powerful persistence
* Works in IE8+, Firefox, Chrome
* Reponsive design


## Installation / Usage

To install, run: `npm i -S @annotationhub/react-golden-layout`.

If you are using webpack or another module bundler, you may wish to install it as dev-dep instead. 
We are shipping an UMD version, an ES5 + ES-Module version and an ES2015+ES-Module version of the library within the package.
Modern bundlers such as webpack should pick up the ES2015 version and transpile the code according to your applications configuration.

## Demo App

We have a demo application embedded within this repository, to run it, run:

```sh
git clone github.com/golden-layout/golden-layout
cd golden-layout
npm ci # (or npm i, if you use an old npm version)
npm run start-jquery
# the app is served at localhost:3000 and uses hot-reload, so you can hack right away within the library and the application.
```

## Development

Internally, we are using webpack and babel to have a build process. 
To get started, follow the steps described in demo-app. 
You can get a complete build by running `npm run build`, which will compile all versions of the app into the `dist` folder.

