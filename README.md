# How to change default port for GitLab
As suggested on https://github.com/gitlabhq/gitlabhq/issues/6581 you can configure port on below file.

Change port to 81 (You can choose your own) at port: near by production:$base >> gitlab: for file /opt/gitlab/embedded/service/gitlab-rails/config/gitlab.yml
Change your host address if you like to use different from your ip address or localhost
Change server port to 81 in file *"/opt/gitlab/embedded/conf/nginx.conf"*
Restart gitlab using command "sudo gitlab-ctl restart".
After applying all above changes still my nginx was running on port 80 only and not sure why also reconfiguring gitlab reset may all change on gitlab.yml files. Finally, file "/etc/gitlab/gitlab.rb" make this work for me. 


Open "/etc/gitlab/gitlab.rb" to text editor where currently I have external_url 'http://myipaddress/' as text. I just change to 
external_url 'http://gitlab.com.local:81/'
then reconfigure using command "sudo gitlab-ctl reconfigure" and voila, Gitlab is now working on port 81.
Hope this help.
