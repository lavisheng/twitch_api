# libtwitch-rs [![crates.io version][1]][2] ![GNU AGPLv3][agpl-logo]
A Rust library for the Twitch API.

# Contributing
Help for this project is highly appreciated. This was built against an older version of the Twitch API. 
Some updates are necessary to work with the latest version of the API. 
Take a look into the [issues](https://github.com/simonsan/libtwitch-rs/issues) if you want to contribute to the project.

Fork it, implement your changes and make a Pull-Request against the `feature-dev` branch of this repo. 

# Usage
```
use libtwitch_rs;
use libtwitch_rs::users;

...

let mut c = libtwitch_rs::new(String::from(CLIENTID));
c.set_oauth_token(TOKEN);

if let Some(user) = match users::get(&c) {
    Ok(r)  => { assert!(r.email.is_some()); Some(r) },
    Err(r) => { println!("{:?}", r); assert!(false); None }
    } {
    let user_id = user.id.to_string();

    match users::get_by_id(&c, &user_id) {
        Ok(r)  => assert_eq!(r.name, user.name),
        Err(r) => { println!("{:?}", r); assert!(false); }
    }
}
```

# Useful Links

- [Token generator](https://twitchtokengenerator.com/)
- [Token test, infos incl. Channel_ID](https://codepen.io/Alca/pen/VwwazOK)
- [Achieve Authorization for a bot](http://web.archive.org/web/20191016034229/https://d-fischer.github.io/twitch-chat-client/docs/examples/basic-bot.html)
- [Twitch API GUide](https://dev.twitch.tv/docs/api/guide)


# License
GNU AGPL-3.0-or-later; see [copying.md](copying.md) and [legal/AGPL-v3](legal/AGPL-v3).


[1]: https://img.shields.io/crates/v/libtwitch-rs.svg?style=flat-square
[2]: https://crates.io/crates/libtwitch-rs
[agpl-logo]: https://www.gnu.org/graphics/agplv3-88x31.png
