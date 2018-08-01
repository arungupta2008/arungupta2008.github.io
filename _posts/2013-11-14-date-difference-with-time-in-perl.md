---
id: 221
title: Date difference with Time in (Perl)
date: 2013-11-14T16:34:41+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=221
permalink: /?p=221
dsq_thread_id:
  - "1965182369"
categories:
  - Uncategorized
tags:
  - Linux
  - Perl
  - Scripting
  - Timer
---
<h4 style="text-align: justify;">
  Function validateDateDifference() can validate date difference with time also.
</h4>

<h4 style="text-align: justify;">
  Validation Range is from 1900-01-01 00:00:00 to 2199-12-31 23:59:59
</h4>

<h4 style="text-align: justify;">
  Syntax
</h4>

<h4 style="text-align: justify;">
  validateDateDifference(&#8220;Startdate time&#8221;,&#8221;Enddate time&#8221;,&#8221;dateformat&#8221;)
</h4>

<h4 style="text-align: justify;">
  date format are : mmddyyyy or ddmmyyyy or yyyymmdd<br /> (this function can support these time formats only)
</h4>

<h4 style="text-align: justify;">
  Start date syntax : mm-dd-yyyy or dd-mm-yyyy or yyyy-mm-dd<br /> you can replace &#8220;-&#8221; with &#8220;.&#8221; or &#8220;/&#8221;<br /> for Ex. mm.dd.yyyy or mm/dd/yyyy<br /> time syntax is : HH:MM:SS<br /> EX. 19:10:59
</h4>

<h4 style="text-align: justify;">
  Test cases :<br /> validateDateDifference(&#8220;12.12.2013 12:12:58&#8243;,&#8221;12.12.2013 12:12:59&#8243;,&#8221;ddmmyyyy&#8221;)<br /> validateDateDifference(&#8220;2013-01-31 12:12:58&#8243;,&#8221;2013-12-02 12:12:59&#8243;,&#8221;yyyymmdd&#8221;)
</h4>

<h4 style="text-align: justify;">
</h4>

<h4 style="text-align: justify;">
  If you want to validate date only then you can use function validateDateFormat()
</h4>

<h4 style="text-align: justify;">
  validateDateFormat(&#8220;date&#8221; , &#8220;dateformat&#8221;)
</h4>

<h4 style="text-align: justify;">
  syntax same as above
</h4>

<h4 style="text-align: justify;">
  If you want to validate time only then you can use function isvalidtime()
</h4>

<h4 style="text-align: justify;">
  isvalidtime(&#8220;time&#8221;)
</h4>

<h4 style="text-align: justify;">
  time syntax same as above
</h4>

`<br />
sub validateDateFormat{<br />
	$regexmmddyyyy='^(0[1-9]|1[012])[-/.](0[1-9]|[12][0-9]|3[01])[- /.]((?:19|20|21)\d\d)$';<br />
	$regexddmmyyyy='^(0[1-9]|[12][0-9]|3[01])[-/.](0[1-9]|1[012])[- /.]((?:19|20|21)\d\d)$';<br />
	$regexyyyymmdd='^((?:19|20|21)\d\d)[- /.](0[1-9]|1[012])[-/.](0[1-9]|[12][0-9]|3[01])$';<br />
	$date=shift;<br />
	$format = shift;<br />
	if($format eq 'ddmmyyyy'){<br />
		if(eval $date=~$regexddmmyyyy){<br />
			$date = $1;<br />
			$month = $2;<br />
			$year = $3;<br />
			if(isvaliddate($date,$month,$year) eq "true"){<br />
				return $year.$month.$date; # Valid date<br />
			}else{<br />
				return "false"; # Not a valid date<br />
			}<br />
		}<br />
	}elsif($format eq 'mmddyyyy'){<br />
		if(eval $date=~$regexmmddyyyy){<br />
			$date = $2;<br />
			$month = $1;<br />
			$year = $3;<br />
			if(isvaliddate($date,$month,$year) eq "true"){<br />
				return $year.$month.$date; # Valid date<br />
			}else{<br />
				return "false"; # Not a valid date<br />
			}<br />
		}<br />
	}elsif($format eq 'yyyymmdd'){<br />
		if(eval $date=~$regexyyyymmdd){<br />
			$date = $3;<br />
			$month = $2;<br />
			$year = $1;<br />
			if(isvaliddate($date,$month,$year) eq "true"){<br />
				return $year.$month.$date; # Valid date<br />
			}else{<br />
				return "false"; # Not a valid date<br />
			}<br />
		}<br />
	}else{<br />
		return "false"; # Not a valid date<br />
	}<br />
}<br />
## HH:MM:SS is allowed only<br />
sub isvalidtime{<br />
	$time = shift;<br />
	$regexhhmmss='^(0[1-9]|1[0-9]|2[0-3])[:](0[1-9]|1[0-9]|2[0-9]|3[0-9]|4[0-9]|5[0-9])[:](0[1-9]|1[0-9]|2[0-9]|3[0-9]|4[0-9]|5[0-9])$';<br />
	if(eval $time=~$regexhhmmss){<br />
		return "true";<br />
	}else{<br />
		return "false";<br />
	}<br />
}<br />
sub isvaliddate{<br />
	$date = shift;<br />
	$month = shift;<br />
	$year = shift;<br />
	#$date<br />
	#$month<br />
	#$year<br />
    if ($date == 31 and ($month == 4 or $month == 6 or $month == 9 or $month == 11)) {<br />
      return "false"; # 31st of a month with 30 days<br />
    }elsif ($date >= 30 and $month == 2) {<br />
      return "false"; # February 30th or 31st<br />
    } elsif ($month == 2 and $date == 29 and not ($year % 4 == 0 and ($year % 100 != 0 or $year % 400 == 0))) {<br />
      return "false"; # February 29th outside a leap year<br />
    } else {<br />
      return "true"; # Valid date<br />
    }<br />
}<br />
sub validateDateDifference{<br />
$startdate = shift;<br />
$enddate = shift;<br />
$format =shift;<br />
# Trimming dates and time   " 20-01-2013 12.58.1 "  --> "20-01-2013 12.59.32"<br />
$startdate =~ s/^\s+|\s+$//g;<br />
$enddate =~ s/^\s+|\s+$//g;<br />
$format=~ s/^\s+|\s+$//g;<br />
($startdate, $startdate_time) = split(/ +/, $startdate);<br />
($enddate, $enddate_time) = split(/ +/, $enddate);<br />
$startdate = validateDateFormat($startdate,$format);<br />
if($startdate eq "false"){<br />
	return "false"; # invalid date difference<br />
}<br />
$enddate = validateDateFormat($enddate,$format);<br />
if($enddate eq "false"){<br />
	return "false"; # invalid date difference<br />
}<br />
#converting into YYYYMMDD format<br />
if($enddate == $startdate ){</p>
<p>	if(isvalidtime($startdate_time) eq "false"){<br />
                        print "reached";<br />
		return "false";<br />
	}<br />
	if(isvalidtime($enddate_time) eq "false"){<br />
        print "reached";<br />
		return "false";<br />
	}<br />
	$startdate_time =~ s/://g;<br />
	$enddate_time =~ s/://g;<br />
	if($startdate_time < $enddate_time){
		return "true"; # Valid date difference 
	}else{
		return "false"; # invalid date difference 
	}
}
elsif($enddate > $startdate ){<br />
	return "true"; # Valid date difference<br />
}else{<br />
	return "false"; # invalid date difference<br />
}<br />
}<br />
print  'validateDateDifference("12.12.2013 12:12:58","12.12.2013 12:12:59","ddmmyyyy")\t'.validateDateDifference("12.12.2013 12:12:58","12.12.2013 12:12:59","ddmmyyyy")."\n";<br />
print 'validateDateDifference("12.12.2014 12:12:58","12.12.2014 12:12:12","ddmmyyyy")\t'.validateDateDifference("12.12.2014 12:12:58","12.12.2014 12:12:12","ddmmyyyy")."\n";<br />
print 'validateDateDifference("12.12.2013 12:12:58","12.12.2013 12:12:59","mmddyyyy")\t'.validateDateDifference("12.12.2013 12:12:58","12.12.2013 12:12:59","mmddyyyy")."\n";<br />
print 'validateDateDifference("12.12.2013 12:12:58","12.12.2013 12:12:59","mmmmyyyy")\t'.validateDateDifference("12.12.2013 12:12:58","12.12.2013 12:12:59","mmmmyyyy")."\n";<br />
print 'validateDateDifference("2013-01-31 12:12:58","2013-12-02 12:12:59","yyyymmdd")\t'.validateDateDifference("2013-01-31 12:12:58","2013-12-02 12:12:59","yyyymmdd")."\n";<br />
print 'validateDateDifference("2013-01-31 12:12:58","2013-12-02 12:12:59","yyyymmdd")\t'.validateDateDifference("2013-01-31 12:12:58","2013-12-02 12:12:59","yyyymmdd")."\n";<br />
`