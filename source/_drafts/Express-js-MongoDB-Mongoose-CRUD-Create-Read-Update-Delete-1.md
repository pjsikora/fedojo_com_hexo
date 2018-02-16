---
title: Express.js / MongoDB / Mongoose CRUD (Create Read Update Delete)
id: 1131
categories:
  - Uncategorized
tags:
---

Ive been working for the last time on small CMS based on Node.js / MongoDB / Express.js / Angular 2\. It's very interesting experience when you still want to improve some features and want to create own system. In this case I had few content types which needs to have CRUD (Create Read Update Delete) feature. Everytime you want to create a controller for your CRUD you need to repeat basic functionalities like for "create":

Model:

    const mongoose = require('mongoose');
    const Schema = mongoose.Schema;

    const schema = new Schema({
      title: String,
      content: String,
    });

    module.exports = mongoose.model('Post', schema);
    `</pre>

    Router:
    <pre class="line-numbers language-js">`const express = require('express');
    const router = express.Router();
    const PostController = require('./controllers/PostController');

    router.post('/posts', PostController.create);

    module.exports = router;
    `</pre>

    Controller:
    <pre class="line-numbers language-js">`const Post = require('./Post');

    const Ctrl = {
      create: function (req, res) {
        let post = new Post();

        post.title = req.body.title;
        post.content = req.body.content;

        post.save(function (err, el) {
          if (err) {
            res.json({success: false, error: err});
          } else {
            res.json({success: true});
          }
        });
      }
    };

    module.exports = Ctrl;
    