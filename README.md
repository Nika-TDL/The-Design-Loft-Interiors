THE DESIGN LOFT INTERIORS - WEBSITE UPLOAD GUIDE
================================================

WHAT IS IN THIS FOLDER
  index.html     the website (this is the home page)
  style.css      the design and layout
  script.js      the behaviour (slider, forms, animations)
  reviews.json   approved client comments shown in "The Client Perspective"
  images/        all photos
  video/         the landing page video

HOW TO PUT IT ON YOUR DOMAIN
  Upload everything INSIDE this folder (not the folder itself) to the main
  folder of your hosting, usually called  public_html  or  www.
  Keep the folder structure exactly as it is. index.html must sit at the top.
  Ways to upload: your hosting's File Manager (cPanel / hPanel: Upload, or
  upload the .zip and choose Extract), or an FTP program such as FileZilla.

  Simple alternative: Netlify or Cloudflare Pages - drag this folder onto the
  page, then add your domain in their Domain settings.

MAKING THE FORMS WORK (feedback + start-your-project form)
  By default both forms open the visitor's email app, addressed to
  admin@thedesignloft.ae. To receive messages directly in your inbox instead:
    1. Create a free form at https://formspree.io (use admin@thedesignloft.ae).
    2. Copy the form address, it looks like  https://formspree.io/f/abcdwxyz
    3. Open script.js in a text editor, find the line near the top
           window.TDL={formEndpoint:""};
       and paste the address between the quotes. Save and upload again.

SHOWING CLIENT REVIEWS ON THE WEBSITE
  Feedback arrives in your email. Review it, and add the ones you approve to
  reviews.json in this format (one block per review, comma between blocks):

  [
    { "name": "Client name", "rating": 5, "text": "Their comment here." },
    { "name": "Another client", "rating": 4, "text": "Another comment." }
  ]

  rating is a number from 1 to 5 (stars). name may be left as "".
  Upload the updated reviews.json. The slider arrows appear automatically
  once there are two or more reviews.

SHOWING REVIEWS AUTOMATICALLY (anyone can post, even anonymously)
  The website can store and show feedback by itself using a free Google Sheet.
  Visitors need no account. Their review appears right away under
  "The Client Perspective" for everyone. Set it up once (about 5 minutes):
    1. Go to https://sheets.google.com and create a blank spreadsheet
       (name it e.g. "Design Loft Reviews").
    2. In the sheet menu choose Extensions > Apps Script.
    3. Delete the sample code, open the file google-apps-script.gs from this
       folder, copy ALL of it and paste it in. Click Save.
    4. Click Deploy > New deployment. Click the gear icon and choose "Web app".
       Execute as: Me.   Who has access: Anyone.   Click Deploy.
       Approve the Google permission screens (Advanced > Go to project).
    5. Copy the "Web app URL" (it starts with https://script.google.com/macros/s/...).
    6. Open script.js, find the line near the top
           window.TDL={formEndpoint:"",reviewsEndpoint:""};
       and paste the URL between the quotes of reviewsEndpoint. Save and upload again.
  Reviews are saved in the sheet's "Reviews" tab, and you get an email for
  each new one. To hide a review, type  no  in its "Show" column.
  Reviews are published immediately without approval, so check the sheet now and then.

NOTES
  - Turn on HTTPS / SSL in your hosting panel (free on most hosts).
  - The page loads its fonts from Google Fonts, so visitors need internet.
