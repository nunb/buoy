

# Module buoy_client #
* [Data Types](#types)
* [Function Index](#index)
* [Function Details](#functions)

<a name="types"></a>

## Data Types ##




### <a name="type-backlog_size">backlog_size()</a> ###


<pre><code>
backlog_size() = pos_integer() | infinity
</code></pre>




### <a name="type-buoy_resp">buoy_resp()</a> ###


<pre><code>
buoy_resp() = #buoy_resp{state = body | done, body = undefined | binary(), content_length = undefined | non_neg_integer(), headers = undefined | [binary()], reason = undefined | binary(), status_code = undefined | 100..505}
</code></pre>




### <a name="type-buoy_url">buoy_url()</a> ###


<pre><code>
buoy_url() = #buoy_url{host = <a href="#type-host">host()</a>, hostname = <a href="#type-hostname">hostname()</a>, path = <a href="#type-path">path()</a>, port = <a href="inet.md#type-port_number">inet:port_number()</a>, protocol = <a href="#type-protocol_http">protocol_http()</a>}
</code></pre>




### <a name="type-client_option">client_option()</a> ###


<pre><code>
client_option() = {ip, <a href="inet.md#type-ip_address">inet:ip_address()</a> | <a href="inet.md#type-hostname">inet:hostname()</a>} | {port, <a href="inet.md#type-port_number">inet:port_number()</a>} | {protocol, <a href="#type-protocol">protocol()</a>} | {reconnect, boolean()} | {reconnect_time_max, <a href="#type-time">time()</a> | infinity} | {reconnect_time_min, <a href="#type-time">time()</a>} | {socket_options, [<a href="gen_tcp.md#type-connect_option">gen_tcp:connect_option()</a> | <a href="gen_udp.md#type-option">gen_udp:option()</a>]}
</code></pre>




### <a name="type-client_options">client_options()</a> ###


<pre><code>
client_options() = [<a href="#type-client_option">client_option()</a>]
</code></pre>




### <a name="type-host">host()</a> ###


<pre><code>
host() = binary()
</code></pre>




### <a name="type-hostname">hostname()</a> ###


<pre><code>
hostname() = binary()
</code></pre>




### <a name="type-path">path()</a> ###


<pre><code>
path() = binary()
</code></pre>




### <a name="type-pool_option">pool_option()</a> ###


<pre><code>
pool_option() = {backlog_size, <a href="#type-backlog_size">backlog_size()</a>} | {pool_size, <a href="#type-pool_size">pool_size()</a>} | {pool_strategy, <a href="#type-pool_strategy">pool_strategy()</a>}
</code></pre>




### <a name="type-pool_options">pool_options()</a> ###


<pre><code>
pool_options() = [<a href="#type-pool_option">pool_option()</a>]
</code></pre>




### <a name="type-pool_size">pool_size()</a> ###


<pre><code>
pool_size() = pos_integer()
</code></pre>




### <a name="type-pool_strategy">pool_strategy()</a> ###


<pre><code>
pool_strategy() = random | round_robin
</code></pre>




### <a name="type-protocol">protocol()</a> ###


<pre><code>
protocol() = shackle_ssl | shackle_tcp | shackle_udp
</code></pre>




### <a name="type-protocol_http">protocol_http()</a> ###


<pre><code>
protocol_http() = http | https
</code></pre>




### <a name="type-state">state()</a> ###


<pre><code>
state() = #state{buffer = binary(), requests_in = non_neg_integer(), requests_out = non_neg_integer()}
</code></pre>




### <a name="type-time">time()</a> ###


<pre><code>
time() = pos_integer()
</code></pre>

<a name="index"></a>

## Function Index ##


<table width="100%" border="1" cellspacing="0" cellpadding="2" summary="function index"><tr><td valign="top"><a href="#handle_data-2">handle_data/2</a></td><td></td></tr><tr><td valign="top"><a href="#handle_request-2">handle_request/2</a></td><td></td></tr><tr><td valign="top"><a href="#init-0">init/0</a></td><td></td></tr><tr><td valign="top"><a href="#setup-2">setup/2</a></td><td></td></tr><tr><td valign="top"><a href="#terminate-1">terminate/1</a></td><td></td></tr></table>


<a name="functions"></a>

## Function Details ##

<a name="handle_data-2"></a>

### handle_data/2 ###

<pre><code>
handle_data(Data::binary(), State::<a href="#type-state">state()</a>) -&gt; {ok, [{pos_integer(), term()}], <a href="#type-state">state()</a>} | {error, atom(), <a href="#type-state">state()</a>}
</code></pre>
<br />

<a name="handle_request-2"></a>

### handle_request/2 ###

<pre><code>
handle_request(X1::term(), State::<a href="#type-state">state()</a>) -&gt; {ok, non_neg_integer(), iodata(), <a href="#type-state">state()</a>}
</code></pre>
<br />

<a name="init-0"></a>

### init/0 ###

<pre><code>
init() -&gt; {ok, <a href="#type-state">state()</a>}
</code></pre>
<br />

<a name="setup-2"></a>

### setup/2 ###

<pre><code>
setup(Socket::<a href="inet.md#type-socket">inet:socket()</a>, State::<a href="#type-state">state()</a>) -&gt; {ok, <a href="#type-state">state()</a>}
</code></pre>
<br />

<a name="terminate-1"></a>

### terminate/1 ###

<pre><code>
terminate(State::<a href="#type-state">state()</a>) -&gt; ok
</code></pre>
<br />

