# mongoose-rattle-plugin [![Build Status](https://secure.travis-ci.org/daemon1981/mongoose-rattle-plugin.png)](https://travis-ci.org/daemon1981/mongoose-rattle-plugin)

## Prerequisite

Your project must be with mongoose 3.8.x. Otherwise you'll have conflicts and it will not work.

## Description

Add social interactions (messages and likes) to mongoose document.

You can :
 - like/unlike the document
 - add/remove comments to the document
 - add/remove replies to a comment
 - like/unlike a comment or a reply

## Installation

```bash
$ npm install mongoose-rattle-plugin
```

## Overview

### Add the plugin to a schema

```javascript
var mongoose           = require('mongoose');
var MongooseRattlePlugin = require('mongoose-rattle-plugin');

var MySchema = new mongoose.Schema();

MySchema.plugin(MongooseRattlePlugin);

MySchema.add({
  'myPersonalField': String
});

var MyModel = mongoose.model("MyModel", MySchema);

module.exports = MyModel;
```

### Specifying Custom UserSchemaName and UserIdType

If the name of your User model schema is not "User" or the User's id type is not `Schema.Types.ObjectId`, you can specify those as options to the plugin:

```javascript
MySchema.plugin(MongooseRattlePlugin, { UserSchemaName: 'UserModel', UserIdType: Some.Other.Type });
```


### Specifications

Please see the [specifications here](https://github.com/daemon1981/mongoose-rattle-plugin/blob/master/test-unit.md)

## Schema architecture choice

### [Embedding All Comments](http://docs.mongodb.org/ecosystem/use-cases/storing-comments/)

### No recursive embedded (threaded) comments

Recursive comments is not so interesting for user experience and brings development much more difficult when requiring performance.

I think threaded discussions are difficult to follow and doesn't reflect real discussion (or civilized discussion).
In real life when a group of people discuss about a subject in civilized society, they stay together in circle and keep talking one after another.
While threaded comments should results to a group of people having a discussion confused in different circles where every could participate. That could be interesting but this a mess.

But if you want to develop recursive comments here are interesting links:
[http://stackoverflow.com/questions/7992185/mongoose-recursive-embedded-document-in-coffeescript](http://stackoverflow.com/questions/7992185/mongoose-recursive-embedded-document-in-coffeescript)
[http://stackoverflow.com/questions/17416924/create-embedded-docs-with-mongoose-and-express](http://stackoverflow.com/questions/17416924/create-embedded-docs-with-mongoose-and-express)

## Contribution prerequisite

```bash
$ npm install -g mocha coffee-script
$ npm install
$ make test
```
