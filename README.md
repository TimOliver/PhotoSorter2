# MediaSorter

While I use iCloud Photos as sort of intermediate buffer, I archive all of the photos I take on my Synology NAS (which is then backed up to Backblaze).

Unfortunately, when exporting photos from Apple's ecosystem, whether it be by dumping from an iPhone, or exporting the originals from Apple Photos, the photos are usually grouped together in a single folder, with completely arbitrary file names. This is especially true of Apple Photos that internally renames image files to UUID strings.

In order to organize these potentially large buckets of photos into a better folder layout for my NAS, I've written this small utility in Swift. It loops through a single folder full of photos and videos, extracts the date they were taken from their EXIF data, and sorts them into folders split up by months and years. The files are given reliable, reproducible file names, so if the same photo exists in separate buckets, they're very easy to find.

Photos and videos that were captured together as Live Photos are also kept together, by having the file name include the Live Photo's UUID.

# Usage

1. Clone or download this repo to your Mac.
2. From the command line, navigate to the downloaded folder.
3. Run `swift run MediaSorter -s /path/to/unsorted/photos/folder -d /path/to/sorted/photos/folder`

# Rationale

I originally wrote [my first photo sorting utility](https://github.com/TimOliver/PhotoSorter) back in 2018, back when Swift 4 was brand new. I was still an absolute n00b at Swift back then (I might still be a n00b now!) and I pretty quickly cobbled that old codebase together very haphazardly.

I decided to do a complete rewrite here to see how I would solve the same problem again. The biggest problem with the older utility was that it didn't reliably keep Live Photo photos and videos together; it simply relied on them having the same file names. This time around, I found [an amazing blog post](https://www.limit-point.com/blog/2018/live-photos/) that documented how Live Photos have an embedded ID in them, and used that as the basis for renaming all of these files in a reproducible way.

I'm always open to feedback! Please let me know what you think of this code, and if you have any suggestions, let me know. Thanks!

# License

This code is released under The Unlicense. It is free and unencumbered software released into the public domain.

Please see [LICENSE](LICENSE) for more information.
