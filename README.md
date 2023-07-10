<!DOCTYPE html>
<html lang="en">

<body>
    <h1>Deploy this Website from GitHub Repo on Ubuntu + Nginx</h1>
    <ol>
        <li>
            <h2>Install Nginx</h2>
            <p>Open the terminal and run the following commands:</p>
            <pre><code>sudo apt update
sudo apt install nginx</code></pre>
        </li>
        <li>
            <h2>Clone the GitHub Repository</h2>
            <p>Clone the GitHub repository containing your website:</p>
            <pre><code>git clone https://github.com/abdelhak-zaaim/al_amarah.git</code></pre>
        </li>
        <li>
            <h2>Move Website Files</h2>
            <p>Move the website files (HTML, CSS, JavaScript, and any other assets) to the appropriate location:</p>
            <pre><code>sudo mv your-repo/* /var/www/html</code></pre>
        </li>
        <li>
            <h2>Set Ownership and Permissions</h2>
            <p>Set the correct ownership and permissions for the website directory:</p>
            <pre><code>sudo chown -R www-data:www-data /var/www/html
sudo chmod -R 755 /var/www/html</code></pre>
        </li>
        <li>
            <h2>Configure Nginx</h2>
            <p>Open the default Nginx configuration file:</p>
            <pre><code>sudo nano /etc/nginx/sites-available/default</code></pre>
            <p>Inside the file, replace the <code>server</code> block with the following configuration:</p>
            <pre><code>server {
    listen 80;
    listen [::]:80;
    
    root /var/www/html;
    index index.html index.htm;
    
    server_name your_domain.com;
    
    location / {
        try_files $uri $uri/ =404;
    }
}</code></pre>
            <p>Replace <code>your_domain.com</code> with your actual domain name or IP address.</p>
        </li>
        <li>
            <h2>Test and Restart Nginx</h2>
            <p>Test the Nginx configuration for any syntax errors:</p>
            <pre><code>sudo nginx -t</code></pre>
            <p>If everything is fine, you should see a "syntax is okay" message.</p>
            <p>Restart Nginx to apply the changes:</p>
            <pre><code>sudo service nginx restart</code></pre>
        </li>
        <li>
            <h2>Access Your Website</h2>
            <p>Your website should now be accessible through your domain name or IP address. Open a web browser and enter your domain name or IP address to see your website.</p>
        </li>
    </ol>
</body>
</html>
