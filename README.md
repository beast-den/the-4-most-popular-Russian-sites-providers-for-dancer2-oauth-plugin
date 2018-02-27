# vkontakte-and-odnoklassniki-providers-for-dancer2-oauth-plugin
A hardly rewritten Facebook provider to work with two Russian social networks - VKontakte and Odnoklassniki. And a slightly modified Providers package of this http://search.cpan.org/~blom/Dancer2-Plugin-Auth-OAuth-0.13/lib/Dancer2/Plugin/Auth/OAuth.pm plugin for Dancer2 framework.

I liked the plugin pretty much when used it with my webpage. But it was unable to handle with Russian sites mentioned above. I made an effort to make the plugin work with those two. Fortunately, I have succeded, and now can publish my efforts. I hope someone may find them useful.

Configuration of Vk and Ok is as simple as all other supported providers. Just copy VKontakte.pm and Odnoklassniki.pm into Providers directory and replace Providers.pm with my version and add something like the following to your providers and you all set. So here is my working configuration of the whole plugin:

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
      VKontakte: # https://vk.com
        tokens:
          client_id: '...'
          client_secret: '...'
        fields: 'first_name,last_name,about,bdate,city,country,photo_max_orig,sex,site'
        api_version: '5.8'
      Odnoklassniki: # https://ok.ru
        tokens:
          client_id: '...'
          client_secret: '...'
          application_key: '...'
        method: 'users.getCurrentUser'
        format: 'json'
        fields: 'email,name,gender,birthday,location,uid,pic_full'
</pre>

As you can see there's not much difference between Vk and Ok and famous Facebook and Google+. Though, it's been a headache to turn Facebook.pm in two more working packages. 
