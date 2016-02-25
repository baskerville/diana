#! /bin/sh

usage() {
	printf '%s [-h|-d DOWNLOAD_DIR|-s SECRET_TOKEN|-u USERNAME|-p PASSWORD] start|stop\n' "${0##*/}"
}

download_dir=${DIANA_DOWNLOAD_DIR:-${XDG_DOWNLOAD_DIR:-${HOME}}}
secret_token=$DIANA_SECRET_TOKEN
username=""
password=""

while getopts 'hd:s:u:p:' opt ; do
	case "$opt" in
		h)
			usage
			exit 0
			;;
		s)
			secret_token=$OPTARG
			;;
		d)
			download_dir=$OPTARG
			;;
		u)
			username=$OPTARG
			;;
		p)
			password=$OPTARG
			;;
	esac
done

shift $((OPTIND - 1))

if [ $# -ne 1 ] ; then
	usage
	exit 1
fi

daemon_pid=/tmp/diana-daemon.pid

case "$1" in
	start)
		# If diana daemon pid file is found
		if [ -e "$daemon_pid" ] ; then
			# remove pid file if referenced process id is not running
			if ! ps -p $(cat "$daemon_pid") > /dev/null 2>&1 ; then
	    			rm -f $daemon_pid
	  		# otherwise just exit
	  		else
				printf '%s\n' 'The daemon is already running.' >&2
				exit 1
			fi
		fi

		XDG_DATA_HOME=${XDG_DATA_HOME:-${HOME}/.local/share}
		diana_session=${XDG_DATA_HOME}/diana.session

		[ ! -e "$diana_session" ] && touch "$diana_session"

		args='--daemon --enable-rpc --continue'
		[ -n "$secret_token" ] && args="$args --rpc-secret $secret_token"
		[ -n "$username" ] && args="$args --rpc-user $username"
		[ -n "$password" ] && args="$args --rpc-passwd $password"

		aria2c $args --dir "$download_dir" --input-file "$diana_session" --save-session "$diana_session"

		pgrep -n -x aria2c > "$daemon_pid"

		if [ $? -ne 0 ] ; then
			printf '%s\n' 'The daemon failed to start.' >&2
			rm -f "$daemon_pid"
			exit 1
		fi
		;;
	stop)
		if [ ! -e "$daemon_pid" ] ; then
			printf '%s\n' 'The daemon is not running.' >&2
			exit 1
		fi

		kill $(cat "$daemon_pid") > /dev/null 2>&1

		if [ $? -ne 0 ] ; then
			printf '%s\n' 'Could not stop the daemon.' >&2
			exit 1
		else
			rm -f "$daemon_pid"
		fi
		;;
esac
