# Description

Docker container and Debian package build process for latest release version of [Caddy web server](https://github.com/mholt/caddy).



            {{ getenv "LISTENADDR" "0.0.0.0"}}:{{ getenv "PORT" "443" }} {
	    root /var/www/public
	    gzip
	    {{ getenv "PROXY" ""}}
            proxy / {{ getenv "BACKENDS" }}  {
		    {{ getenv "INSECURESKIPVERIFY" "insecure_skip_verify" }}
		    policy round_robin
		    {{ getenv "HEALTHCHECK" "" }}
	    }
	    tls {{ getenv "TLS" "self_signed" }}
	    templates
