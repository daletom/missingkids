# Prismic Slice Contest Submission
This is part of the Prismic Slice contest.

> For info the contest [blog post](https://prismic.io/blog/slice-contest?utm_campaign=devexp&utm_source=github&utm_medium=slicecontestpost).

Here is a link to the Storybook of the [custom mocks](https://missingkids-slicecontest.tomdale.vercel.app/?path=/story/missingimage--default-slice) I created.

Here is a link to a live version of a [website](https://missingkids.tomdale.website/) using all of this.

## Why Create Slices for a Missing Kids site?

I've always thought that certain aspects of websites that focus on missing people could be better. In particular, when images get indexed to google, they will not usually have all the pertinent info you need or even know these are images of missing children. So I figured that while I was working on designing new slices for a Prismic Contest, might as well try to find a solution to this problem.  Prismic allowed me to easily create a UI for end users that simply add an image, name, description, other info and I was able to embed that into the image so the image can be indexed by Google. Then when someone sees the image on Google, it will have all the necessary info about the missing child.  You always hear that it's just important to get these pictures out there and to have as many people look at them, so I think this will particulary help this effort and ensure important info is not lost when the images are indexed away from the website.

## Documentation

The storybook was made using Prismic as part of their #slicecontest. You will notice a lot of the changes I made to the prismic images are using an API that is part of imgix. Prismic does natively use imgix for their images for sizes, compression, formatting, & responsive design. But there are a lot of tricks you can do around styling & design to the image as well. Below, you will see explanations of how I applied this using the imgix API in conjunction with Prismic.

Here is a basic example of modifying a `<prismic-image :field="slice.primary.image" />`:

```
<img :src="slice.primary.image.url + 'insert-imgix-api'" />
```

So if I wanted to add a watermark of an image coming from a prismic field in the slice called waterMarkImage and I always wanted the size of the watermark to be 25% of the size of the main image, I could do it like this:
```
<img :src="slice.primary.image.url + 'mark-w=.25&mark=' + slice.primary.waterMarkImage.url">
```
Here is more info on watermark in the [imgix Documentation](https://docs.imgix.com/apis/rendering/watermark/mark). I hope this gives a basic idea of what I am going to be doing in the following.

### Creating Polaroid Style Images

I wanted to create polaroid style photos. They are actually pretty simple to make, you can just add padding around the photo, but the key is that on the bottom the padding needs to be larger. You can certainly use css to do this, but I wanted to do this with imgix so the image that is indexed later in google still looks like this. I set a general padding number, then a larger pad-bottom number, and then declared what color I wanted these padded areas to be. Below is the imgix API I used to create the padding to make it look like a polaroid photo:
```
pad-bottom=75&pad=10&bg=E8E8EB 
```
Then I begin adding different sizes to the image, add a missing "stamp" as a blend, then create a text field at the bottom of the image in the same style I did above as a watermark, but fill that area with a rich text field from a prismic slice.

![code snippet example](https://images.prismic.io/missingkids/bcf43dba-baa4-4e77-8f96-edf0e6978b4e_missingimgcode.png?auto=compress,format&w=640&h=480&fit=fill&fill=solid&fill-color=CBD5E0)

Ultimately, I am creating an image that looks like this: 

![polaroid example](https://images.prismic.io/missingkids/c670e6b4-5274-4094-b025-15b6ce69f223_polaroid.jpg?w=300)

I know creating the image string seems difficult, but the primary goal is to put all of this important info into the image so when it is indexed in google, it will not be lost. Once this is setup correctly in the slice, it is extremely easy to use in the prismic dashboard when creating pages. Other people may do similar ideas like this to make og:images that are tweeted stand out with text, logos, etc.  

## ☑️ &nbsp;Submission Checklist

To keep track of your progress and to be sure not to miss anything here's a simple checklist you can use. Once everything ticks you should be ready to submit your library to us by tagging [@prismicio](https://twitter.com/prismicio) with #SliceContest on Twitter.

- [X] My library contains at least **5 different slices**
- [X] I have updated the [LICENSE](./LICENSE) to credit myself for my library
- [X] The Storybook documentation is hosted here: https://github.com/daletom/missingkids#documentation 
- [X] My library does not contain any non-public licensed assets


