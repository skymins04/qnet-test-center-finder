# [q-net 시험장 검색 자동화 스크립트]

크롬에서 q-net 자격증시험 접수 장소선택 페이지를 띄우고 지역을 전체로 맞춰놓은 뒤,
브라우저개발자 도구를 켜서 콘솔창에 아래 텍스트 묶음(1, 2, 3번)을 순차적으로 붙여 넣어주세요
자리가 비어있는 시험장을 발견하면 'find'라는 알림창이 뜨며 종료되므로, 바로 접수 버튼을 눌러 낚아채세요

===========

1. jQuery 로드

var jq = document.createElement('script'); jq.src = "https://ajax.googleapis.com/ajax/libs/jquery/2.1.4/jquery.min.js"; document.getElementsByTagName('head')[0].appendChild(jq);

===========

2. 충돌 방지

jQuery.noConflict();

===========

3. 자동화 루틴

var loop = setInterval(() => {
    getAreaList(this.form, '1', 'viewList')
    if($('div.tbl_type4 table tbody tr').length != 1 && $('div.tbl_type4 table tbody tr').not('.end_aly').length !== 0) {
        alert('found center(s)');
        clearInterval(loop);
    }
    else {
        console.log('not found');
    }
}, 100);
