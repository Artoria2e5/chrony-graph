This is for graphing logs from chrony.  See the branch "ntpd" for ntpd/ntpsec graphs

Packages needed:

	perl-DateTime
	liberation-sans-fonts
	gnuplot (needs Cairo/Pango support for best graphs)
	bc

To setup:

	cp bin/copy-to-website.example bin/copy-to-website
	# edit bin/copy-to-website to copy the files to your website
	cp titles.example titles
	# edit titles to have the IPs and hostnames of your remote clocks
	cp -a runX run1
	# edit run1/index.html.tmpl to show the graphs for the IPs of the remote clocks
	# edit bin/run if your logdir is different: LOGDIR=/var/log/chrony

You probably also want to configure your webserver to serve .gz files with the correct Content-Encoding, or to compress .svg on-the-fly

To run (under screen/tmux):

	cd run1 ; ../bin/loop
	# edit run1/notes to keep notes

To run (under cron):

	0 * * * * /path/to/chrony-graph/run1/run-cron

Optional scripts:

	run1/startime - echo the unix timestamp to start at
	run1/custom-plot - generate some custom plots
	bin/copy-logfiles - download the logfiles from elsewhere, see copy-logfiles.example
