# the-4-most-popular-Russian-sites-providers-for-dancer2-plugin-auth-oauth
A hardly rewritten 'Facebook.pm' provider to work with four Russian sites - VKontakte [https://vk.com], Odnoklassniki [https://ok.ru], Mail.ru [https://mail.ru] and Yandex [http://www.yandex.ru]. And a slightly modified 'Provider.pm' package of this http://search.cpan.org/~blom/Dancer2-Plugin-Auth-OAuth-0.13/lib/Dancer2/Plugin/Auth/OAuth.pm plugin for Dancer2 framework.

I liked the plugin pretty much when used it with my webpage. But it was unable to handle with Russian sites mentioned above. I made an effort to make the plugin work with those four. Fortunately, I have succeded, and now can publish my efforts. I hope someone may find them useful.

Configuration is as simple as all other supported providers. Just copy the files to their appropriate locations and you all set. So here is my working configuration of the plugin:

<pre>
plugins:
  'Auth::OAuth':
    prefix: '/auth'
    success_url: '/'
    error_url: '/'
    providers:
      Facebook:
        tokens:
          client_id: '...'
          client_secret: '...'
        fields: 'id,email,name,gender,birthday,location,picture.width(320)'
      Google:
        tokens:
          client_id: '...'
          client_secret: '...'
      Twitter:
        tokens:
          consumer_key: '...'
          consumer_secret: '...'
      VKontakte:
        tokens:
          client_id: '...'
          client_secret: '...'
        fields: 'first_name,last_name,about,bdate,city,country,photo_max_orig,sex,site'
        api_version: '5.8'
      Odnoklassniki:
        tokens:
          client_id: '...'
          client_secret: '...'
          application_key: '...'
        method: 'users.getCurrentUser'
        format: 'json'
        fields: 'email,name,gender,birthday,location,uid,pic_full,url_profile'
      MailRU:
        tokens:
          client_id: '...'
          client_private: '...'
          client_secret: '...'
        method: 'users.getInfo'
        format: 'json'
        secure: 1
      Yandex:
        tokens:
          client_id: '...'
          client_secret: '...'
        format: 'json'
</pre>

Please, send me feedback on problems discovered, but remember I've made 4 Russian sites providers only. This magnificient plugin was written by another person. Use CPAN search to get more information.
