[![Build Status](https://travis-ci.org/sul-dlss/spotlight-resources-iiif.svg?branch=master)](https://travis-ci.org/sul-dlss/spotlight-resources-iiif) [![Coverage Status](https://coveralls.io/repos/sul-dlss/spotlight-resources-iiif/badge.svg?branch=master&service=github)](https://coveralls.io/github/sul-dlss/spotlight-resources-iiif?branch=master) [![Dependency Status](https://gemnasium.com/sul-dlss/spotlight-resources-iiif.svg)](https://gemnasium.com/sul-dlss/spotlight-resources-iiif) [![Gem Version](https://badge.fury.io/rb/spotlight-resources-iiif.png)](http://badge.fury.io/rb/spotlight-resources-iiif)

# Spotlight::Resources::Iiif

Spotlight Resource Indexer for IIIF manifests or collections.

## Installation

Add this line to your blacklight-spotlight Rails application's Gemfile:

```ruby
gem 'spotlight-resources-iiif'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install spotlight-resources-iiif

Run the generator:

    $ bundle exec rails generate spotlight:resources:iiif:install

## Configuration

The resource indexer stores the URL to the IIIF manifest in the `content_metadata_iiif_manifest_ssm` field by default.  This can be configured to be a different field in an initializer by setting `Spotlight::Resources::Iiif::Engine.config.iiif_manifest_field`.

### Customizing Metadata

By default Spotlight-Resources-IIIF will store the data in the manifest's `description`, `attribution`, and `license` attributes.  Label/value objects in the `metadata` attribute will also be stored. If your `metadata` attribute has some other data structure, you can provide your own class to parse the `metadata` attribute by configuring the `Spotlight::Resources::Iiif::Engine.config.metadata_class` (put a reference to the class in a lambda).

This class will receive a `IIIF::Presentation::Manifest` object and must return a hash with label/value pairs in the `#to_solr` method. These label/value pairs will be turned into exhibit custom fields based on their label.

## Usage

This is a Rails engine gem to be used along with blacklight-spotlight, another Rails engine gem used to build exhibits sites while leveraging the blacklight Rails engine gem.

This gem adds a IIIF URL option to the New Items via External Resources tab. This form allows curators to input a URL to a IIIF Manifest or collection, and the contents of all the manifests and collections in the hierarchy will be harvested as new items in the Spotlight exhibit.

To start adding content from IIIF go to the Exhibit Dashboard and click on the `Items` link in the Curation section of the sidebar.  Click the `Add Items` button in the items administration screen. In the `From External Resources` tab there will be a `IIIF URL` option. Enter the URL to a IIIF manifest or collection in the URL field and click the `Add IIIF Items` button.  Once indexing is complete you will see new documents in the exhibit for every collection and manifest represented in the provided URL.

![add-iiif-item](https://cloud.githubusercontent.com/assets/96776/12284218/f4987eaa-b962-11e5-9602-cd5a769b4cec.gif)

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/sul-dlss/spotlight-resources-iiif.

## Contributing

1. Fork it (https://help.github.com/articles/fork-a-repo/)
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request (https://help.github.com/articles/using-pull-requests/)
