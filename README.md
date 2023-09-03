# Moonamick components

DisplayContent
-

This component will inject all the copys and images of a determined section

You can add it to a page using the backend editor or directly in your code

```
[displayContent]
section = "home"
```

Once the component is added to a page or partial the global objects **moonCopy** and **moonImage** will be available for use:

### moonCopy


```{{ moonCopy['copy-slug'].text }}```

Example: 

```
<div class="resume text-center">
    <div class="container">
        <h2>{{ moonCopy['title-about-us'].text }}</h2>
        {{ moonCopy['about-us'].text |md }} //notice you can combine with other twig filters
    </div>
</div>
```

### moonImage

```{{ moonImage['image-slug'].path }}```


Example

```
<img src="{{ moonImage['footer-logo'].path }}" width="363">
```

Additionally, the moonImage has three more properties for each image, useful for SEO

```
{{ moonImage['image-slug'].name }}

{{ moonImage['image-slug'].title }}

{{ moonImage['image-slug'].description }}
```

Example

```
<img src="{{ moonImage['footer-logo'].path }}" alt="{{ moonImage['footer-logo'].description }}" title="{{ moonImage['footer-logo'].title }}">
```

moonDeck
-

>The Deck of cards is useful when you need a block of information than shares structure, for example a pool of services, products or team information.

![image](https://github.com/Polilla-Studio/moonamick-plugin-pub/assets/8864253/093979fa-8f04-4924-ba27-25ba84924761)



This component will inject a deck of cards. You can add it to a page or component using the backend editor or directly in to the code

```
[getDeck]
slug = "deck-slug"
```

The elements available in the moonDeck object are:

```
moonDeck.name
moonDeck.title
moonDeck.text
moonDeck.cards
```

in order to use the cards in the frontend you can use a ```for loop```

```
<div class="row">
	<div class="col-lg-12">{{ moonDeck.title }}</div>
	<div class="col-lg-12">{{ moonDeck.text }}</div>
    {% for card in moonDeck.cards %} //each card of the team
        <div class="col-lg-4">
            <span>{{card.title |md}}</span>
            <img src="{{ card.image.path }}" title="{{ card.image.title }}" alt="{{ card.image.description }}">
            <span>{{ card.description }}</span>
        </div>
    {% endfor %}
</div>
```

As you notice in the example, the ```moonDeck.card.image``` comes with title and description variables useful for SEO

```
card.image.title

card.image.description
```

Card variables available

```
card.title
card.text
card.url
card.url_text
card.image.path
card.image.title
card.image.description
card.reverse_image.path
card.reverse_image.title
card.reverse_image.description
```

getPool
-
>The Pool of images is a simplified version of the deck of cards. This component is useful when you need to group images with a few information, for example, a group of logos or a small gallery

![Captura de pantalla 2023-09-03 a la(s) 16 42 52](https://github.com/Polilla-Studio/moonamick-plugin-pub/assets/8864253/4de4a81b-b7d2-4a57-91ef-7ea329963058)


This component will inject a pool of images. You can add it to a page or component using the backend editor or directly in to the code

```
[getPool]
slug = "pool-slug"
```

```
<div class="container">
    <h2>{{ moonPool.title }}</h2>
    <p>{{ moonPool.text }}</p>
    <div class="client-logos">
    {% for image in moonPool.images %}
        <img src="{{ image.path }}" title="{{image.title}}" alt="{{image.description}}">
    {% endfor %}
    </div>
</div>
```
