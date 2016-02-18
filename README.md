# movement app backend

Dev environment:

* yum --enablerepo=epel  (on AWS: sudo rpm -Uvh http://download.fedoraproject.org/pub/epel/7/x86_64/e/epel-release-7-5.noarch.rpm)
* yum install python-pip python-psycopg2 pandoc
* pip install --upgrade pip
* pip install requests pyYAML BeautifulSoup Elasticsearch Flask flask-httpauth git+https://github.com/dgrtwo/ParsePy.git pytz
* curl -s https://www.parse.com/downloads/cloud_code/installer.sh | sudo /bin/bash

edit /opt/bernie/config.yml (sample http://pastebin.com/bA6SskLp)

Elasticsearch mapping for events -- run this on your ES instance before loading with the sync

curl -XPUT http://localhost:9201/events_en_v1 -d '{"mappings":{"berniesanders_com":{"properties":{"location":{"type":"geo_point"},"attendee_count":{"type":"long"},"capacity":{"type":"long"},"date":{"type":"string"},"description":{"type":"string"},"event_id":{"type":"string"},"event_id_obfuscated":{"type":"string"},"event_type_name":{"type":"string"},"is_official":{"type":"boolean"},"lang":{"type":"string"},"latitude":{"type":"double"},"longitude":{"type":"double"},"name":{"type":"string"},"object_type":{"type":"string"},"site":{"type":"string"},"event_date":{"type":"date","format":"date_optional_time"},"status":{"type":"long"},"timestamp_creation":{"type":"date","format":"date_optional_time"},"timezone":{"type":"string"},"url":{"type":"string"},"uuid":{"type":"string"},"venue":{"properties":{"address1":{"type":"string"},"address2":{"type":"string"},"city":{"type":"string"},"name":{"type":"string"},"state":{"type":"string"},"zip":{"type":"string"}}},"venue_address1":{"type":"string"},"venue_address2":{"type":"string"},"venue_address3":{"type":"string"},"venue_city":{"type":"string"},"venue_name":{"type":"string"},"venue_state":{"type":"string"},"venue_zip":{"type":"string"}}}}},"articles_en_v1":{"mappings":{"berniesanders_com":{"properties":{"_id":{"type":"string"},"article_category":{"type":"string"},"article_id":{"type":"string"},"article_type":{"type":"string"},"body":{"type":"string"},"body_html":{"type":"string"},"body_html_nostyle":{"type":"string"},"description":{"type":"string"},"description_html":{"type":"string"},"excerpt":{"type":"string"},"excerpt_html":{"type":"string"},"image_url":{"type":"string"},"lang":{"type":"string"},"object_type":{"type":"string"},"site":{"type":"string"},"status":{"type":"long"},"timestamp_creation":{"type":"date","format":"date_optional_time"},"timestamp_publish":{"type":"date","format":"date_optional_time"},"title":{"type":"string"},"url":{"type":"string"},"uuid":{"type":"string"}}}}},"videos_v1":{"mappings":{"youtube_com":{"properties":{"description":{"type":"string"},"description_snippet":{"type":"string"},"object_type":{"type":"string"},"site":{"type":"string"},"status":{"type":"long"},"thumbnail_url":{"type":"string"},"timestamp_creation":{"type":"date","format":"date_optional_time"},"timestamp_publish":{"type":"date","format":"date_optional_time"},"title":{"type":"string"},"uuid":{"type":"string"},"video_id":{"type":"string"}}}}}'
