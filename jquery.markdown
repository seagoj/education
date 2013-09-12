# jQuery

## jQuery Air: Captain's Log
* [Level 1: Events](#level-1-events)
* [Level 2: Ajax](#level-2-ajax)
* [Level 3: Effects](#level-3-effects)
* [Level 4: Code Organization](#level-4-code-organization)

### [Level 1: Events](http://jquerytwo.codeschool.com/levels/1)
#### Reading from the DOM
    
    <section id='tabs'>
        <ul>
            <li><a href='#2012-09-27' data-flights="6">Sep 27</a></li>
            <li><a href='#2012-09-28' data-flights="5">Sep 28</a></li>
            <li><a href='#2012-09-29' data-flights="5">Sep 29</a></li>
        </ul>
    </section>

    $('#tabs ul:first').html();                 // <a href='#2012-09-27' data-flights="6">Sep 27</a>
    $('#tabs ul:first a').text();               // Sep 27
    $('#tabs ul li.first a').attr('href');      // #2012-09-27
    $('#tabs ul li:first a').data('flights');   // 6


##### .preventDefault()
* prevents the browser from performing the default actions on the specified object
* used frequently for anchor clicks

##### Functions
Functions work as expected without the $(this) keyword needing to be passed. Jquery handles that.

##### namespacing the '$' to JQuery

    jQuery(function($) {
        ...
    });

* ensures contained code is referring to jQuery
* replaces $(document).ready()

##### choosing nth li

    $("#tabs li:eq(2)") // refers to 3rd li; index starts at 0

##### .bind()

    $("tabs li a").click(changeTab);
    $("tabs li a").mouseenter(showNumberOfFlights);
    $("tabs li a").mouseleave(hidenumberOfFlights);

    // Becomes ...

    $("tabs li a").bind({
        click: changeTab,
        mouseenter: showNumberOfFlights,
        mouseleave: hideNumberOfFlights
    });

### <a id='2'></a>[Level 2: Ajax](http://jquerytwo.codeschool.com/levels/2)
#### Error handling and callbacks

    // initialize fetchingFlights
    var fetchingFlights = null;

    function showFlights(activeDiv) {
        // hide the current data being displayed
        $("#tabs div").hide();

        // check to see if ajax is currently running; abort if so
        if(fetchingFlights) {
            fetchingFlights.abort();
        }

        fetchingFlights = $.ajax('/flights', {
                // data: object of values to be passed to the script
                data: { date: activeDiv },
                // cache: set to false to keep browsers from caching
                cache: false,
                // timeout: time in miliseconds to wait for call to return before error
                timeout: 8000,
                // beforeSend: commands to issue prior to sending call to script
                beforeSend: function(result) {
                    $('#error').hide();
                    $('#loading').show();
                },
                // complete: commands to issue upon completion
                complete: function() {
                    $('#loading').hide();
                    fetchingFlights = null;
                },
                // success: commands to issue upon success
                success: function(result) {
                    $(activeDiv).html(result);
                    $(activeDiv).show();
                },
                // error: commands to issue upon failure
                error: function(result) {
                    // make sure that error was not due to abort
                    if(result.statusText != "abort") {
                        $('#error').show();
                    }
                }
            }
        });
    }

#### Fetching data using JSON

    function selectFlight(e) {
        e.preventDefault();
        $("#tabs a.selected").removeClass('selected');
        $(this).addClass('selected');

        var flight = $(this).data('flight');
        var flightClass = $(this).data('class');

        $('#confirm').hide();

        $.ajax('/flights/'+flight, {
            data: { 'class': flightClass },
            // dataType: defines the scripts return type, in this case json
            dataType: 'json',
            success: showTotal
        });
    }

    function showTotal(json) {
        $('#price').text(json.price);
        $('#fees').text(json.fees);
        $('#total').text(json.price+json.fees);
        $('confirm').slideDown();
    }

#### Fetching data using JSONP

    // Use jsonp dataType for json calls to remote servers
    function remoteJSON(e) {
        ...

        $.ajax('page', {
            ...
            dataType: jsonp,
            ...
        });
    }

#### Pulling email and password

    function login(e) {
        e.preventDefault();
        $('#login h4').slideUp();

        // serialize: creates an object from the post names and variables
        var form = $(this).serialize();

        $.ajax('/login', {
            data: form,
            // return type set to javascript, so it may be executed upon return
            dataType: 'script',
            // specifying a post instead of a get request
            type: 'post'
        });
    }

### <a id='3'></a>[Level 3: Effects](http://jquerytwo.codeschool.com/levels/3)
#### Chaining & Adjusting Speed
    // effects that are chained together run sequentially; the below would fadeOut and then back in
    $('#DOMobj').fadeOut().html().fadeIn();

    // callbacks make sure that each step is completed before the next beigins
    $('#DOMobj').fadeOut('fast', function() {
        $this.html.fadeIn('slow');
    });


#### Animating with CSS
    // animate a height change
    $('#DOMobj').css({'background-color':'#2C1F11'})
                .animate({height:'30'});

    // animate text flash
    $('#DOMobj').css({'opacity':'0.5'})
                .animate({opacity:1}, 'slow');

#### Effect Easing
* Easing defines the rate of shange
* Swing is default: fast then slow
* Linear is constant speed

#### Using a Queue
    $('#login').queue(function(next) {
        $(this).html("...").fadIn( function () {
            $('#confirm .confirm-purchase').slideDown(500, 'linear');
            $("...").css({'background-color':'#2c1f11', 'oacity':'0.5'})
                    .animate({ opacity:'1', height:'30'});
            });
            next();
    });

#### Adding a Delay
    function showTooltip(e) {
        var num_flights = $(this).data('flights');
        $(this).append("<span class='tooltip'>"+num_flights+" flights</span>");
        $("#tabs span.tooltip").delay(300).fadeIn();
    }

#### Stopping an Effect
    // stop() stops the animation on the object immediately
    function hideTooltip(a) {
        $("#tabs span.tooltip").stop().fadeOut(function(){
            $(this).remove();
        });
    }

### <a id='4'></a>[Level 4: Code Organization](http://jquerytwo.codeschool.com/levels/4)
#### Each & Map Utility Methods
    fetchingFlights = $.ajax('/flights.json', {
        data: { date: activeDiv },
        ...
        success: function(result) {
            $(activeDiv + ' tbody td').remove();

            var rows = "";
            $.each(flights, function(index, flight) {
                rows += "<tr>" +
                    "<td>" + flight.depart + "</td>" +
                    "<td>" + flight.arrive + "</td>" +
                    ... +
                    "</tr>";
            });

            $(activeDiv + ' tbody').html(rows);

            // or using $.map

            var flight_rows = $.map(flights, function(flight) {
                return "<tr>" +
                    "<td>" + flight.depart + "</td>" +
                    "<td>" + flight.arrive + "</td>" +
                    ... +
                    "</tr>";
            });
            $(activeDiv + ' ').html(flight_rows.join(''));
        }
    });

#### Creating your own utility functions
    // hello world utility function
    (function($){
        $.hello = function() {
            alert("Hello there!");
        };
    })(jQuery)

    // Usage
    $.hello();

#### Creating plugins
    // sample plugin definition
    (function($){
        $.fn.callOut = function(options) {
            var defaults = {
                duration: fast
            }
            var options = $.extend(defaults, options);
            this.css({ opacity:0.5}).animate({opacity:1}, options.duration);
        };
    })(jQuery)        

    // usage
    $(activeDiv).callOut();
    // or
    $(activeDiv).callOut({'duration': 'fast'});

    // Add tooltip plugin
    $.fn.addTooltip = function(options) {
        var defaults = {
            outDuration: slow,
            inDuration: fast
        }
        var options = $.extend(defaults, options);

        return this.bind({
            mouseenter: function(e) {
                var tip = $(this).data('tooltip');
                $("<span class='tooltip'>" + tip + "</span>")
                    .appendTo(this).delay(100).fadeIn(options.inDuration);
            },
            mouseleave: function(e) {
                $(this).find('span.tooltip').stop().fadeOut(options.outDuration, function() {
                    $(this).remove();
                });
            }
        });
    }

    // Usage
    $("#tabs ul li a").addTooltip();
    // or
    $("#tabs ul li a").addTooltip({"inDuration": 1000, "outDuration": 1000});


#### Encapsulating your code
    // example object
    var selectFlights = {
        fetchingFlights : null;
        currentFlights : null;

        // init: loads all jQuery that has to be in place when the page loads
        init : function() {
            $("#tabs ul li a").click(selectFlights.changeTab);
            $("#tabs div").delegate("#flights a", "click", selectFlights.selectFlight);
        },
        showFlights : function(activeDiv) {...},
        changeTab : function(e) {...},
        selectFlight : function(e) {...}
    };

    var confirmFlight = {
        showTotal : function(json) {...},
        login : function(e) {...}
    };

    selectFlights.init();

#### Custom Events
    // Sample event that switches that selects tabs when the number keys are pressed
    $("#tabs ul li a").bind({
        'selectTab': function(e) {

        }
    });

    $(document).keydown(function(e)) {
        if(e.keyCode >= 49 && e.keyCode <=53) {
            var numSelected = e.keyCode-49;
            var tabSelected = $("#tabs ul li:eq(" + numSelected + ") a");
            $("#tabs ul li:eq("+ tabSelected +") a").trigger('selectTab');
        }
    }

#### jQuery Templates
    // Defining a template in HTML
    // must download and pull in the source
    <script src="jquery.tmpl.js" type="text/javascript"></script>
    <script id='flightTemplate' type='text/x-jquery-tmpl'>
        <tr>
            <td>${depart}</td>
            <td>${arrive}</td>
            <td>${flight}</td>
            <td>
                {{if (routing == 0)}}
                    Nonstop
                {{else (routing ==1)}}
                    1 Stop
                {{else}}
                    ${routing} Stops
                {{/if}}
            </td>
            <td>
                <a href='#' data-flight-'${flight}' data-class='first_class'>
                    ${first-class}
                </a>
            </td>
            <td>
                <a href='#' data-flight-'${flight}' data-class='economy'>
                    ${economy}
                </a>
            </td>
        </tr>
    </script>

    // Calling a template in jQuery
    // flights is a json array
    $('#flightTemplate').tmpl(flights)
                        .appendTo(activeDiv+' tbody');

    // Syntax
    ${<field name>}         // print text
    ${html <field name>}    // print markup
    {{each}}                // iterate of data array if json contains an array
    {{tmpl}}                // include other template
