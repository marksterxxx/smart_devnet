# Smart Developer Network API 

Ruby wrapper for REST API of SMART Developer Network.

## Requirements

    Ruby 1.9.x

## Installation

Add this line to your application's Gemfile:

    gem 'smart_devnet'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install smart_devnet


## Usage

    SmartDevnet.configure do |config|
      config.sp_id = ''
      config.sp_password = ''
      config.nonce = ''
      config.created_at = ''
      config.access_code = ''
      config.sp_service_id = ''
      config.path_to_cert = ''
    end

    sms = SmartDevnet.send_sms('+63xxx', 'Testing API.')

    unless sms.error?

      sms.check_status
      unless sms.error?
        puts sms.status['+63xxx']
      else
        puts sms.error
      end

    else
      puts sms.error
    end

    sms = SmartDevnet.send_sms('+63xxx', 'Testing API with client notification.', 'http://...')

    puts sms.error if sms.error?


    subs = SmartDevnet.subscribe('+639', 'http://...')
    if subs.error?
      puts subs.error
    else
      puts subs.subscription_id
    end

    subs.unsubscribe
    puts subs.error if subs.error?


    subs2 = SmartDevnet.unsubscribe(subs.subscription_id)
    puts subs2.error if subs2.error?

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## MIT Open Source License

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

## Acknowledgements

This was created by <a href="http://blog.bridgeutopiaweb.com" target="_blank">Katherine G. Pe</a>.
