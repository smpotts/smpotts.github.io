---
layout: page
title: Contact
cover-img: /assets/img/granada.jpg
---

<form action="mailto:shelby@shelbypotts.com" method="post" enctype="text/plain" style="font-family:'Lora','Times New Roman',serif; max-width:600px;">

  <label for="name" style="font-weight:bold;">Name:</label><br>
  <input type="text" id="name" name="name" required 
         style="width:100%; padding:8px; margin-bottom:15px;"><br>

  <label for="email" style="font-weight:bold;">Email:</label><br>
  <input type="email" id="email" name="email" required 
         style="width:100%; padding:8px; margin-bottom:15px;"><br>

  <label for="subject" style="font-weight:bold;">Subject:</label><br>
  <input type="text" id="subject" name="subject" required 
         style="width:100%; padding:8px; margin-bottom:15px;"><br>

  <label for="message" style="font-weight:bold;">Message:</label><br>
  <textarea id="message" name="message" rows="6" required 
            style="width:100%; padding:8px; margin-bottom:15px;"></textarea><br>

  <button type="submit" 
          style="padding:10px 20px; font-weight:bold; cursor:pointer; 
                 font-family:'Open Sans','Helvetica Neue',Helvetica,Arial,sans-serif;">
    Send
  </button>
</form>