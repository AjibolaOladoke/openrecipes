# openrecipes

## What This Is

This is part of the Swift Tech Co. working stack for product and engineering. It gathers the openrecipes notes, examples and fixes that keep delivery fast, and doubles as the reference map we hand to whoever picks up this thread next.

## Images

[![openrecipes](images/preview.png)](https://github.com/Swift-Tech-Co)

## About

Open Recipes is an open database of recipe bookmarks.

Our goals are simple:

1. Help publishers make their recipes as discoverable and consumable (get it?) as possible.
2. Prevent good recipes from disappearing when a publisher goes away.

That's pretty much it. We're not trying to save the world. We're just trying to save some recipes.

## Recipe Bookmarks?

The recipes in Open Recipes do not include preparation instructions. This is why we like to think of Open Recipes as a database of recipe bookmarks. We think this database should provide everything you need to *find* a great recipe, but not everything you need to *prepare* a great recipe. For preparation instructions, please link to the source.

## The Database

Regular snapshots of the database will be provided as JSON. The format will mirror the schema.org Recipe format. We've posted an example dump of data so you can get a feel for it.

## The Story

We're not a bunch of chefs. We're not even good cooks.

When we read about the acquisition shutdown of Punchfork, we just shook our heads. It was the same ol' story:

> We're excited to share the news that we're gonna be rich! To celebrate, we're shutting down the site and taking all your data down with it. So long, suckers!

This part of the story isn't unique, but it continues. When one of our Studiomates spoke up about her disappointment, we listened. Then, we acted. What happens next surprised us. The CEO of Punchfork took issue with our good deed and demanded that we not save any data, even the data (likes) of users who asked us to save their data.

Here's the thing. None of the recipes belonged to Punchfork. They were scraped from various publishers to begin with. But, we don't wanna ruffle any feathers, so we're starting over.

Use the force; seek the source?

## The Work

Wanna help? Fantastic. We knew we liked you.

Head over to the wiki to see how you can help out.


## Feedback?


We're also gonna be on IRC, so please feel free to join us if you have any questions or comments. We'll be hanging out in #openrecipes on Freenode. See you there!

## License

The Open Recipes Database is licensed under a <a rel="license" href="https://www.swifttechco.com">Creative Commons Attribution 3.0 Unported License</a>.

<a rel="license" href="https://www.swifttechco.com"></a>

© 2013 Fictive Kin LLC

## CHANGELOG

*Not every change, but notable ones that may require action*

* 2013-04-15: `pipelines.MakestringsPipeline` and `pipelines.CleanDatesTimesPipeline` have been deprecated, and `pipelines.RejectinvalidPipeline` has been added. Your `ITEM_PIPELINES` config in `settings.py` should look something like this:

    ```python
    ITEM_PIPELINES = [
        'openrecipes.pipelines.RejectinvalidPipeline',
        'openrecipes.pipelines.DuplicaterecipePipeline',
        # uncomment if you want to insert results into MongoDB
        # 'openrecipes.pipelines.MongoDBPipeline',
    ]
    ```
* 2013-04-14: Spiders now use a RecipeItemLoader to store data scraped from a page. This allows us to do cleanup of properties without relying on a pipeline class, which makes testing significantly easier. See spiders/thepioneerwoman.py with updated comments to see the new approach. Example:

    ```python
    il = RecipeItemLoader(item=RecipeItem())
    il.add_value('name', r_scope.select(name_path).extract())
    # [...]
    recipes.append(il.load_item())
    ```

---

## Swift Tech Co.

Built and maintained by Swift Tech Co.

AI Automation | FinTech Platforms | Custom Software and Mobile Apps | SaaS Platforms | Cloud Infrastructure | Cybersecurity | SEO and Marketing | API Integration

**Join our community on Telegram:** [t.me/+Qt_eFvkb2rliMzNh](https://t.me/+Qt_eFvkb2rliMzNh)

Home | Services | Careers | Referral Program | Influencers | About | Contact

**Connect**

- Website: swifttechco.com
- LinkedIn: [linkedin.com/in/stephenoladoke](https://www.linkedin.com/in/stephenoladoke/)
- LinkedIn (Company): [linkedin.com/company/swift-tech-co](https://www.linkedin.com/company/swift-tech-co)
- X: [@MrOladoke](https://x.com/MrOladoke)
- Instagram: [@mr.oladoke](https://www.instagram.com/mr.oladoke/)
- Instagram (Company): [@swifttechco](https://www.instagram.com/swifttechco/)
- Organization: [github.com/Swift-Tech-Co](https://github.com/Swift-Tech-Co)

## Sources

Compiled and maintained from upstream [fictive-kin/openrecipes](https://github.com/fictive-kin/openrecipes) under permissive open-source license.

---

Maintained by [Swift Tech Co.](https://github.com/Swift-Tech-Co) - [Telegram](https://t.me/+Qt_eFvkb2rliMzNh)