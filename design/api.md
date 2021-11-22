# META4d Market API Design

app

- oauth
- getToken
- getInfo
    - return {userid}
- generateAvatar(type)
    - type: gif, png, ...
    - return {type:url|blob, content:url|blob}

site

- bind(appid, app_oauth_token, address, sig)
    - throw app_already_bound_exception
    - return token2
- refresh_token(appid, app_oauth_token, address, sig)
    - throw app_not_bound_exception
    - return token2
- unbind(token2, address, sig)
- get_nft_count (token2, type)
    - type: showroom, wardrobe
    - return [token_id...]
- get_nfts (token2, type, <offset>, <num>)
    - return [token_id...]
- get_nft_info(token_id)
    - return {token_meta}
        - token_meta: {item_id, meta, url}
- get_nft_resource(token_id)
    - return byte_blob
- get_nft_resource_url(token_id)
    - return url
- put_on(token2, [token_id...])
    - throw token_id_not_in_wardrobe_exception, token_id_not_available, token_not_owned
- take_off(token2, [token_id...])
    - throw token_id_not_on_exception, token_id_not_available, token_not_owned
- publish_token(token2, [{token_meta}])
    - token_meta: {item_id, meta}
    - return [token_id]
- expire_token(token2, [token_id...])

market

- sell
- cancel
- buy