<!DOCTYPE html>
<html lang="en">

<body>
    <h1>Deploying this Website on Ubuntu + Nginx</h1>
    <ol>
        <li>
            <h2>Install Nginx</h2>
            <p>Open the terminal and run the following commands:</p>
            <pre><code>sudo apt update
sudo apt install nginx</code></pre>
        </li>
        <li>
            <h2>Start Nginx</h2>
            <p>Once Nginx is installed, start the service:</p>
            <pre><code>sudo service nginx start</code></pre>
        </li>
        <li>
            <h2>Create Website Directory</h2>
            <p>Create a directory to store your website files. For example, let's create a directory called "my-website":</p>
            <pre><code>sudo mkdir /var/www/my-website</code></pre>
        </li>
        <li>
            <h2>Move Website Files</h2>
            <p>Move your website files (HTML, CSS, JavaScript, and any other assets) to the newly created directory:</p>
            <pre><code>sudo cp -r /path/to/your/website/* /var/www/my-website</code></pre>
        </li>
        <li>
            <h2>Set Ownership and Permissions</h2>
            <p>Set the correct ownership and permissions for the website directory:</p>
            <pre><code>sudo chown -R www-data:www-data /var/www/my-website
sudo chmod -R 755 /var/www/my-website</code></pre>
        </li>
        <li>
            <h2>Configure Nginx</h2>
            <p>Open the default Nginx configuration file:</p>
            <pre><code>sudo nano /etc/nginx/sites-available/default</code></pre>
            <p>Inside the file, you'll find a <code>server</code> block. Replace its contents with the following configuration:</p>
            <pre><code>server {
    listen 80;
    listen [::]:80;
perl
Copy code
root /var/www/my-website;
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
<p>If everything is fine, you should see "syntax is okay" message.</p>
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
