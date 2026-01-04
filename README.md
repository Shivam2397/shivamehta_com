# Shivam Mehta - Portfolio Website

A modern, elegant, and professional portfolio website for Shivam Mehta - Full Stack Developer & Software Engineer.

## Features

- 🎨 Modern and elegant design
- 📱 Fully responsive (mobile, tablet, desktop)
- ⚡ Fast and lightweight
- 🖼️ Profile picture upload functionality
- 🎯 Smooth scrolling and animations
- 📧 Contact form ready for integration
- ☁️ AWS S3 compatible (static hosting)

## Project Structure

```
website/
├── index.html          # Main HTML file
├── styles.css          # All styles and animations
├── script.js           # JavaScript functionality
├── assets/             # Images and media files
│   └── profile.jpg     # Your profile picture (add here)
└── README.md           # This file
```

## Setup Instructions

### 1. Add Your Profile Picture

1. Place your square profile picture in the `assets/` folder
2. Name it `profile.jpg` (or update the path in `index.html`)
3. Recommended size: 300x300px or larger (square format)
4. Supported formats: JPG, PNG, WebP

Alternatively, you can use the built-in upload feature on the website itself.

### 2. Customize Content

Edit `index.html` to update:
- Personal information (name, location, email, social links)
- About section text
- Project details and descriptions
- Skills and technologies
- Contact information

### 3. Update Contact Information

In `index.html`, update:
- Email address: `shivam.mehta@example.com`
- LinkedIn URL: `https://linkedin.com/in/shivam-mehta`
- GitHub URL: `https://github.com/shivam-mehta`

### 4. Contact Form Integration

The contact form is currently set up for client-side handling. To make it functional, you can integrate with:

- **EmailJS**: Free email service for static sites
- **Formspree**: Simple form backend
- **AWS SES**: For AWS-hosted solutions
- **Netlify Forms**: If using Netlify

See the `script.js` file for integration examples.

## AWS S3 Deployment

### Prerequisites

- AWS Account
- AWS CLI installed and configured
- S3 bucket created

### Step 1: Create S3 Bucket

1. Go to AWS S3 Console
2. Click "Create bucket"
3. Name your bucket (e.g., `shivam-mehta-portfolio`)
4. Choose a region
5. **Uncheck** "Block all public access" (or configure bucket policy)
6. Enable "Static website hosting" in bucket properties

### Step 2: Configure Bucket Policy

Add this bucket policy to allow public read access:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::YOUR-BUCKET-NAME/*"
        }
    ]
}
```

Replace `YOUR-BUCKET-NAME` with your actual bucket name.

### Step 3: Enable Static Website Hosting

1. Go to bucket Properties
2. Scroll to "Static website hosting"
3. Enable it
4. Set:
   - Index document: `index.html`
   - Error document: `index.html` (for SPA routing)

### Step 4: Upload Files

#### Using AWS CLI:

```bash
# Navigate to project directory
cd /path/to/website

# Sync files to S3
aws s3 sync . s3://YOUR-BUCKET-NAME --exclude "*.md" --exclude ".git/*" --exclude ".gitignore"

# Set correct content types
aws s3 cp index.html s3://YOUR-BUCKET-NAME/index.html --content-type "text/html"
aws s3 cp styles.css s3://YOUR-BUCKET-NAME/styles.css --content-type "text/css"
aws s3 cp script.js s3://YOUR-BUCKET-NAME/script.js --content-type "application/javascript"
```

#### Using AWS Console:

1. Go to your S3 bucket
2. Click "Upload"
3. Select all files (index.html, styles.css, script.js, assets folder)
4. Click "Upload"

### Step 5: Access Your Website

Your website will be available at:
```
http://YOUR-BUCKET-NAME.s3-website-REGION.amazonaws.com
```

Or use a custom domain with CloudFront (recommended for production).

## CloudFront Setup (Optional but Recommended)

For better performance and custom domain:

1. Create a CloudFront distribution
2. Set origin to your S3 bucket
3. Configure:
   - Default root object: `index.html`
   - Error pages: 404 → `/index.html` (for SPA routing)
4. Add your custom domain (requires Route 53 or external DNS)

## Custom Domain Setup

1. Get a domain from Route 53 or external provider
2. Create CloudFront distribution (see above)
3. Add CNAME record pointing to CloudFront domain
4. Request SSL certificate in AWS Certificate Manager
5. Attach certificate to CloudFront distribution

## Local Development

Simply open `index.html` in a web browser, or use a local server:

```bash
# Using Python
python3 -m http.server 8000

# Using Node.js (http-server)
npx http-server

# Using PHP
php -S localhost:8000
```

Then visit `http://localhost:8000`

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

## Performance Tips

1. Optimize images before uploading
2. Use WebP format for images when possible
3. Enable CloudFront caching
4. Compress CSS/JS files (optional, for production)
5. Use CDN for fonts (already using Google Fonts CDN)

## Maintenance

- Update project portfolio regularly
- Keep skills section current
- Test contact form functionality
- Monitor S3 bucket costs
- Update dependencies if using any build tools

## Troubleshooting

### Images not loading
- Check file paths are correct
- Ensure images are uploaded to S3
- Verify bucket policy allows public access

### Styles not applying
- Check CSS file is uploaded
- Verify content-type is `text/css`
- Clear browser cache

### JavaScript not working
- Check browser console for errors
- Verify JS file is uploaded
- Ensure content-type is `application/javascript`

### Contact form not working
- Integrate with EmailJS, Formspree, or AWS SES
- Check form action URL is correct
- Verify CORS settings if using external API

## License

© 2024 Shivam Mehta. All rights reserved.

## Support

For issues or questions, please contact:
- Email: shivam.mehta@example.com
- LinkedIn: [linkedin.com/in/shivam-mehta](https://linkedin.com/in/shivam-mehta)
- GitHub: [github.com/shivam-mehta](https://github.com/shivam-mehta)

---

Built with ❤️ for showcasing professional work and skills.

