# My Tech Blog

A Jekyll-based blog about industry developments, experiments, testing new tools, and tutorials.

## Technologies Used

- Jekyll
- GitHub Pages
- Minima theme

## Setup Instructions

### Local Development

1. Install Ruby and Bundler
2. Clone this repository
3. Run `bundle install` to install dependencies
4. Run `bundle exec jekyll serve` to start the local server
5. Visit `http://localhost:4000` in your browser

### Adding New Posts

1. Create a new markdown file in the `_posts` directory
2. Use the following naming convention: `YYYY-MM-DD-title-of-post.md`
3. Add front matter at the top of the file:
   ```yaml
   ---
   layout: post
   title: "Your Post Title"
   date: YYYY-MM-DD HH:MM:SS -0500
   categories: [category1, category2]
   author: Your Name
   ---
   ```
4. Write your post content in Markdown below the front matter

## Categories

The blog is organized into the following categories:

- Industry Developments
- Experiments
- Tools
- Tutorials

## License

This project is licensed under the MIT License - see the LICENSE file for details. 