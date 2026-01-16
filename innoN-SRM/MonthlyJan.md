# 수입시스템 프로젝트

## 일일 업무

### 2025-12-31
 * edi 소스 확인

### 2026-01-02
* 외자구매요청접수(MM)  <  외자구매요청  <  SRM변경  <  수출입  <  Home
    - [x] 품목 선택하고 `외자발주 생성` 클릭 시 이동되는 페이지에서 자재정보 > 자재코드 컬럼 우측에 `조건값 수` 컬럼 추가
    - [x] ESPPODTC 컬럼에 데이터 수를 표시
    - [x] 값 클릭 후 아래 조건정보에 해당 데이터 조회처리
    - `저장` 시 sap 호출
    - 야근 8시

### 2026-01-05
* 외자발주생성/외자발주변경 
 - [x] 결재 최종 승인 시 sap 호출 (저장버튼에 단위테스트)
    * 인터페이스 정의서1 W:\수입시스템 프로젝트\참조자료\SAP_IF관련\SAP_IF_PO_분석(수정).xls
    * 인터페이스 정의서2 W:\수입시스템 프로젝트\수입관리 시스템 산출물 SAMPLE\분석설계\20. 인터페이스사양서\HK이노엔_통합구매시스템_인터페이스정의서_20251216_v10.xls
 - [ ] ~~결재 최종 승인 시 sap 호출 (결재 완료시 호출)~~
 - [ ] `SAP전송` 버튼 클릭으로 sap 호출 
 - 야근 9시 (김치찌게)

### 2026-01-06
 - 오후 출근(졸업식)
 - sap 호출 예외처리 및 테스트(발주, 품목)
 - 결재 테스트 예정
 - 야근 9시 (투썸 샌드위치)
 - 결재 붙이기 
 - [ ] mpr 테스트
 - [ ] poc 발주승인 외자용 만들기 `MPOC`
    * 코드관리 G003코드추가
 - [ ] CACP 발주변경 외자용 만들기 `MCACP`
    * 코드관리 G003코드추가
 - 김밥/라면

### 2026-01-07
 - 오전 단위테스트 동석(업무파악)
 - [ ] sap호출건 개발서버 오류 점검
 - [x] 외자구매요청 결재 테스트
 - [x] 외자발주 결재 테스트
 - [ ] 외자발주 수정 결재 테스트
 - 교촌 치킨버거

### 2026-01-08
 - [x] 발주변경 결재 상신
 - [ ] 발주변경 결재 템플릿 내용 빈것 확인필요
 - [ ] 물대 sap연동
 - [ ] lc 결재 연동
 - [ ] lg 결재 연동
 - 짜장곱

### 2026-01-09
 - [x] 입고 sap연동

### 2026-01-12
 - [x] 발주변경 결재 테스트
 - 짬뽕

### 2026-01-13
 - [x] 비용처리 sap 연계 테스트
 - [ ] 레포트 사용법 숙지
    1. 원격접속 ``` 10.224.110.61/62,  CJSBC\HKNADMIN / HK%sysT!@ ``
    2. 바탕화면 UBIFORM Editor 실행 (로그인 admin/1234)
    * 참고자료
    ```
    w:\수입시스템 프로젝트\참조자료\이노엔 제공 자료\UBIFORM Report 사용설명서.pdf
    w:\수입시스템 프로젝트\참조자료\이노엔 제공 자료\수입신용장 신청서_TradeOne.pdf
    w:\수입시스템 프로젝트\참조자료\이노엔 제공 자료\수입조건변경신청서_TradeOne.pdf
    w:\수입시스템 프로젝트\참조자료\이노엔 제공 자료\수입화물선취보증서_TradeOne.pdf
    발주서샘플 - 계약 및 발주현황  <  계약 및 발주관리  <  계약/발주  <  Home - 발주장세 - 발주서 출력
    ```

### 2026-01-14
 - [ ] lc신용장 1페이지
 - 투썸
 
### 2026-01-15
 - [ ] lc신용장 2페이지
 - 제육볶음

### 2026-01-16
 - [ ] lc변경
 * 레포트 설정  
    - Z(10.224.100.241):\report-SRM\UFile\sys\fonts 폴더에 폰트파일 추가

## 기타
* 백철흠 partuser0274

### EDI
 * [KT-NET EDI문서요청](W:\수입시스템 프로젝트\참조자료\KT-Net 관련자료\KT-NET EDI문서요청 rev1.1.xlsx)
 * [수입솔루션 EDI정리목록](W:\수입시스템 프로젝트\참조자료\KT-Net 관련자료\수입솔루션 EDI정리목록.xlsx)


### 결재
 * G003

 
| 코드 | 명칭 | 사용 | 코드번호 | 비고 |
| --- | --- | ---: | ---: | --- |
| MPR | 외자구매요청 | Y | 944 | N |
| MPOC | 외자발주승인 | Y | 945 | N |
| MCACP | 외자발주변경 | Y | 946 | N |
| LCOPEN | 외자LC개설 | Y | 947 | N |
| ESTLG | 외자L/G 발급 | Y | 948 | N |

* MPR	외자구매요청	Y
``` html
<article>
    <section>
        <table border="1" cellpadding="1" cellspacing="0" style="min-height:100px;">
             <colgroup>
                <col style="width:15%" />
                <col style="width:35%" />
                <col style="width:15%" />
                <col style="width:35%" />
            </colgroup>
            <h3>일반정보 - ${prInfo.pr_no?default("")}</h3>
            <tr>
                <th>사업소</th>
                <td>${prInfo.oper_org_cd_nm?default("")}</td>
                <th>PR번호</th>
                <td>(${prInfo.pr_no?default("")} / ${prInfo.pr_rev?default("")})</td>
            </tr>
            <tr>
                <th>PR일자</th>
                <td>${prInfo.pr_req_date?default("")}</td>
            </tr>
            <tr>
                <th>PR금액</th>
                <td style="text-align: right;">${prInfo.pr_tot_amt?default("")} (${prInfo.cur?default("")})</td>
                <th>PR명</th>
                <td>${prInfo.pr_tit?default("")}</td>
            </tr>
        </table>
        <table border="1" cellpadding="1" cellspacing="0">
             <colgroup>
                <col style="width:5%" />
                <col style="width:10%" />
                <col style="width:15%" />
                <col style="width:10%" />
                <col style="width:10%" />
                <col style="width:10%" />
                <col style="width:10%" />
                <col style="width:10%" />				
            </colgroup>
            <tr>
                <th>항번</th>
                <th style="height:23px">자재코드</th>
                <th style="height:23px">자재명</th>
                <th style="height:23px;width:60px">구매수량</th>
                <th style="height:23px;width:60px">단위</th>				
                <th style="height:23px">PR단가</th>
                <th style="height:23px">PR금액</th>				
                <th style="height:23px">납품장소</th>				
                <th>구매그룹</th>
            </tr>

            &lt;#list prItems as item&gt;
            <tr>
                <th>${item.pr_no?default("")}</th>
                <th style="height:23px">${item.item_cd?default("")}</th>
                <td style="height:23px">${item.item_nm?default("")}</td>
                <th style="text-align: right;height:23px;width:60px">${item.item_qty?default("")}</th>
                <th style="height:23px;width:60px">${item.unit_cd?default("")}</th>				
                <th style="text-align: right;height:23px">${item.pr_price?default("")}</th>
                <th style="text-align: right;height:23px">${item.pr_amt?default("")}</th>				
                <th style="height:23px">${item.rd_locat?default("")}</th>
                <th >${item.purc_grp_nm?default("")}(${item.purc_grp_cd?default("")})</th>
            </tr>
  
            &lt;/#list&gt;
        </table>
        <br><br><hr border="2"><br>
    </section>
</article>
```
* MPOC	외자발주승인	Y
``` html
<article>
    <section>
        &lt;#list poInfo as info&gt;
        <table border="1" cellpadding="1" cellspacing="0" style="min-height:100px;">
             <colgroup>
                <col style="width:15%" />
                <col style="width:35%" />
                <col style="width:15%" />
                <col style="width:35%" />
            </colgroup>
            <h3>일반정보 - ${info.sap_po_no_str?default("")}</h3>
            <tr>
                <th>사업소</th>
                <td>${info.oper_org_cd_nm?default("")}</td>
                <th>발주번호</th>
                <td>(${info.sap_po_no_str?default("")} / ${info.po_rev?default("")})</td>
            </tr>
            <tr>
                <th>발주일자</th>
                <td>${info.po_cre_date2?default("")}</td>
                <th>협력사</th>
                <td>${info.vd_nm?default("")}</td>
            </tr>
            <tr>
                <th>발주금액</th>
                <td style="text-align: right;">${info.po_tot_amt?default("")} (${info.cur?default("")})</td>
                <th>발주명</th>
                <td>${info.po_tit?default("")}</td>
            </tr>
        </table>
        <table border="1" cellpadding="1" cellspacing="0">
             <colgroup>
                <col style="width:5%" />
                <col style="width:10%" />
                <col style="width:15%" />
                <col style="width:10%" />
                <col style="width:10%" />
                <col style="width:10%" />
                <col style="width:10%" />
                <col style="width:10%" />
                <col style="width:10%" />				
            </colgroup>
            <tr>
                <th>항번</th>
                <th style="height:23px">자재코드</th>
                <th style="height:23px">자재명</th>
                <th style="height:23px;width:60px">발주수량</th>
                <th style="height:23px;width:60px">단위</th>				
                <th style="height:23px">발주단가</th>
                <th style="height:23px">발주금액</th>				
                <th style="height:23px">납품일자</th>
                <th style="height:23px">납품장소</th>				
                <th>구매그룹</th>
            </tr>

            &lt;#list info.poItems as item&gt;
            <tr>
                <th>${item.po_lno?default("")}</th>
                <th style="height:23px">${item.item_cd?default("")}</th>
                <td style="height:23px">${item.item_nm?default("")}</td>
                <th style="text-align: right;height:23px;width:60px">${item.item_qty?default("")}</th>
                <th style="height:23px;width:60px">${item.unit_cd?default("")}</th>				
                <th style="text-align: right;height:23px">${item.item_price?default("")}</th>
                <th style="text-align: right;height:23px">${item.item_amt?default("")}</th>				
                <th style="height:23px">${item.rd_date2?default("")}</th>
                <th style="height:23px">${item.rd_locat?default("")}</th>				
                <th >${item.purc_grp_nm?default("")}(${item.purc_grp_cd?default("")})</th>
            </tr>
  
            &lt;/#list&gt;
        </table>
        <br><br><hr border="2"><br>
        &lt;/#list&gt;
    </section>
</article>
```
* MCACP	외자발주변경	Y
``` html
<header>
    <h2>발주변경품의서</h2>
    &lt;#if approvalInfo.aprv_docno?? &gt;
    <h4>( 품의번호 : ${approvalInfo.aprv_docno?default("")} )</h4>
    &lt;/#if&gt;
</header>
<article>
<section>
    	<table>
        	 <colgroup>
                <col style="width:18%" />
                <col style="width:32%" />
                <col style="width:18%" />
                <col style="width:32%" />
            </colgroup>
            <tr>
                <th>기안일자</th>
                <td>${approvalInfo.rpt_dt?default("")}</td>
                <th>기안자</th>
                <td>[${poInfo.oper_org_cd_nm?default("")}] ${approvalInfo.reg_nm?default("")}</td>
            </tr>
        </table>
    </section>
    <section>
        <h3>요청정보</h3>
        <table>
            <colgroup>
                <col style="width:18%" />
                <col style="width:32%" />
                <col style="width:18%" />
                <col style="width:32%" />
            </colgroup>
            <tr>
                <th>계약변경요청자</th>
                <td>${poInfo.mod_req_nm?default("")}</td>
                <th>요청일자</th>
                <td> &lt;#if poInfo.mod_req_date?? &gt; ${poInfo.mod_req_date[0..3]?default("")}/${poInfo.mod_req_date[4..5]?default("")}/${poInfo.mod_req_date[6..7]?default("")}  &lt;/#if&gt;   </td>
            </tr>
            <tr>
                <th>변경사유 </th>
                <td colspan="3">${poInfo.mod_req_cause?default("")}</td>
            </tr>
        </table>
    </section>
<section>
        <h3>기본정보</h3>
        <table>
            <colgroup>
                <col style="width:18%" />
                <col style="width:32%" />
                <col style="width:18%" />
                <col style="width:32%" />
            </colgroup>
            <tr>
                <th>구매운영조직</th>
                <td>${poInfo.oper_org_cd_nm?default("")}</td>
                <th>구매유형</th>
                <td>${poInfo.purc_typ_nm?default("")}</td>
            </tr>
            <tr>
                <th>발주번호 / 차수</th>
                <td>${poInfo.po_no?default("")} / ${poInfo.po_rev?default("")}</td>
                <th>발주명</th>
                <td>${poInfo.po_tit?default("")}</td>
            </tr>
            <tr>
                <th>계약번호</th>
                <td>${poInfo.cntr_no?default("")}</td>
                <th>계약기간</th>
                <td> &lt;#if poInfo.cntr_prd_sd?? && poInfo.cntr_prd_ed?? &gt;  ${poInfo.cntr_prd_sd[0..3]?default("")}/${poInfo.cntr_prd_sd[4..5]?default("")}/${poInfo.cntr_prd_sd[6..7]?default("")} ~ ${poInfo.cntr_prd_ed[0..3]?default("")}/${poInfo.cntr_prd_ed[4..5]?default("")}/${poInfo.cntr_prd_ed[6..7]?default("")}  &lt;/#if&gt; </td>
            </tr>
            <tr>
                <th>내/외자구분</th>
                <td>${poInfo.shipper_type_nm?default("")}</td>
                <th>발주일자</th>
                <td>${poInfo.po_cre_date[0..3]?default("")}/${poInfo.po_cre_date[4..5]?default("")}/${poInfo.po_cre_date[6..7]?default("")}</td>
            </tr>
            <tr>
                <th>협력사 </th>
                <td>${poInfo.vd_nm?default("")}</td>
                <th>협력사담당자</th>
                <td>${poInfo.vd_chr_id?default("")}</td>
            </tr>
            <tr>
                <th>통화 </th>
                <td>${poInfo.cur?default("")}</td>
                <th>기본계약여부</th>
                <td>${poInfo.bas_cntr_yn_str?default("")}</td>
            </tr>
            <tr>
                <th>발주금액 </th>
                <td class="tr">${poInfo.po_tot_amt?default("")}</td>
                <th>전자계약여부</th>
                <td>${poInfo.elec_cntr_yn_str?default("")}</td>
            </tr>
            <tr>
                <th>발주금액(원화) </th>
                <td class="tr">${poInfo.po_exch_amt?default("")}</td>
                <th></th>
                <td></td>
            </tr>
            <tr>
                <th>특약사항 </th>
                <td colspan="3">${poInfo.po_rem?default("")}</td>
            </tr>
        </table>
    </section>
     <section>
        <h3>계약기간</h3>
        <table>
            <colgroup>
                <col style="width:18%" />
                <col style="width:32%" />
                <col style="width:18%" />
                <col style="width:32%" />
            </colgroup>
            <tr>
                <th>계약기간 (변경전)</th>
                <td> &lt;#if previousPoInfo.cntr_prd_sd?? && previousPoInfo.cntr_prd_ed?? &gt;  ${previousPoInfo.cntr_prd_sd[0..3]?default("")}/${previousPoInfo.cntr_prd_sd[4..5]?default("")}/${previousPoInfo.cntr_prd_sd[6..7]?default("")} ~ ${previousPoInfo.cntr_prd_ed[0..3]?default("")}/${previousPoInfo.cntr_prd_ed[4..5]?default("")}/${previousPoInfo.cntr_prd_ed[6..7]?default("")}  &lt;/#if&gt;  </td>
                <th>계약기간 (변경후)</th>
                <td> &lt;#if poInfo.cntr_prd_sd?? && poInfo.cntr_prd_ed?? &gt;  ${poInfo.cntr_prd_sd[0..3]?default("")}/${poInfo.cntr_prd_sd[4..5]?default("")}/${poInfo.cntr_prd_sd[6..7]?default("")} ~ ${poInfo.cntr_prd_ed[0..3]?default("")}/${poInfo.cntr_prd_ed[4..5]?default("")}/${poInfo.cntr_prd_ed[6..7]?default("")} &lt;/#if&gt; </td>
            </tr>
        </table>
    </section>
    <section>
        <h3>지급정보</h3>
        <table>
            <colgroup>
                <col style="width:18%" />
                <col style="width:10%" />
                <col style="width:11%" />
                <col style="width:11%" />
                <col style="width:18%" />
                <col style="width:32%" />
            </colgroup>
            <tr>
                <th>지급방법</th>
                <td colspan="3">계약서표시 : ${poInfo.pay_terms_yn_str?default("")} ${poInfo.pay_terms_cd_nm?default("")}</td>
                <th>지급방법설명</th>
                <td>${poInfo.pay_terms_desc?default("")}</td>
            </tr>
            <tr>
                <th>납품방법</th>
                <td colspan="3">계약서 표시 : ${poInfo.dely_terms_yn_str?default("")} ${poInfo.dely_terms_cd_nm?default("")}</td>
                <th>납품방법설명</th>
                <td>${poInfo.dely_terms_desc?default("")}</td>
            </tr>
            <tr>
                <th>세금코드</th>
                <td colspan="3">${poInfo.tax_cd_nm?default("")}</td>
                <th></th>
                <td></td>
            </tr>
            <tr>
                <th rowspan="3">지불조건</th>
                <td>선급금</td>
                <td class="tr">${poInfo.pre_pay_rate?default(0)} %</td>
                <td class="tr">${poInfo.pre_pay_amt?default(0)}</td>
                <td rowspan="3" colspan="2"></td>
            </tr>
            <tr>
                <td>중도금</td>
                <td class="tr">${poInfo.mid_pay_rate?default(0)} %</td>
                <td class="tr">${poInfo.mid_pay_amt?default(0)}</td>
            </tr>
            <tr>
                <td>잔금</td>
                <td class="tr">${poInfo.bal_pay_rate?default(0)} %</td>
                <td class="tr">${poInfo.bal_pay_amt?default(0)}</td>
            </tr>
            <tr>
                <th>대금지급조건</th>
                <td colspan="5">${poInfo.pay_desc?default("")}</td>
            </tr>
        </table>
    </section>
    <section>
        <h3>계약정보</h3>
        <table>
            <colgroup>
                <col style="width:12%" />
                <col style="width:7%" />
                <col style="width:13%" />
                <col style="width:12%" />
                <col style="width:22%" />
                <col style="width:12%" />
                <col style="width:22%" />
            </colgroup>
            <tr>
                <th>계약금액(VAT포함)</th>
                <td colspan="2" class="tr">${poInfo.cntr_amt?default(0)}</td>
                <th>공급가액</th>
                <td class="tr">${poInfo.supply_amt?default(0)}</td>
                <th>VAT</th>
                <td class="tr">${poInfo.vat_amt?default(0)}</td>
            </tr>
            <tr>
                <th>계약이행보증금</th>
                <td class="tr">${poInfo.perfor_bond_rate?default(0)} %</td>
                <td class="tr">${poInfo.perfor_bond_amt?default(0)}</td>
                <th>계약이행보증기간</th>
                <td colspan="3">${poInfo.perfor_bond_cls_nm?default("")}  &lt;#if poInfo.perfor_bond_sd?? && poInfo.perfor_bond_ed?? &gt; ${poInfo.perfor_bond_sd[0..3]?default("")}/${poInfo.perfor_bond_sd[4..5]?default("")}/${poInfo.perfor_bond_sd[6..7]?default("")} ~ ${poInfo.perfor_bond_ed[0..3]?default("")}/${poInfo.perfor_bond_ed[4..5]?default("")}/${poInfo.perfor_bond_ed[6..7]?default("")} 
            &lt;/#if&gt;  </td>
            </tr>
            <tr>
                <th>선급금이행보증금</th>
                <td class="tr">${poInfo.pre_pay_bond_rate?default(0)}  %</td>
                <td class="tr">${poInfo.pre_pay_bond_amt?default(0)}</td>
                <th>선급금보증기간</th>
                <td colspan="3">${poInfo.pre_pay_bond_cls_nm?default("")} &lt;#if poInfo.pre_pay_bond_sd?? && poInfo.pre_pay_bond_ed?? &gt; ${poInfo.pre_pay_bond_sd[0..3]?default("")}/${poInfo.pre_pay_bond_sd[4..5]?default("")}/${poInfo.pre_pay_bond_sd[6..7]?default("")} ~ ${poInfo.pre_pay_bond_ed[0..3]?default("")}/${poInfo.pre_pay_bond_ed[4..5]?default("")}/${poInfo.pre_pay_bond_ed[6..7]?default("")} 
            &lt;/#if&gt; </td>
            </tr>
            <tr>
                <th>하자이행보증금</th>
                <td class="tr">${poInfo.maint_bond_rate?default(0)} %</td>
                <td class="tr">${poInfo.maint_bond_amt?default(0)}</td>
                <th>하자보증기간</th>
                <td colspan="3">${poInfo.maint_bond_cls_nm?default("")}  &lt;#if poInfo.maint_bond_typ??  &gt; ${poInfo.maint_bond_typ_nm?default("")} 로부터  &lt;/#if&gt; &lt;#if poInfo.maint_bond_mon??  &gt;                ${poInfo.maint_bond_mon?default("")} 개월 &lt;/#if&gt; </td>
            </tr>
            <tr>
                <th>지체상금</th>
                <td>100분의</td>
                <td>${poInfo.delay_rate?default(0)}</td>
                <td colspan="4"></td>
            </tr>            
        </table>
    </section>
    <section>
        <h3>품목정보 (변경전)<span>통화 : ${previousPoInfo.cur?default("")}</span></h3>
        <table class="tc">
            <colgroup>
                <col style="width:5%" />
                <col style="width:10%" />
                <col style="width:30%" />
                <col style="width:7%" />
                <col style="width:12%" />
                <col style="width:12%" />
                <col style="width:12%" />
                <col style="width:12%" />
            </colgroup>
            <tr>
                <th rowspan="2">순번</th>
                <th>품목코드</th>
                <th>품목명</th>
                <th>발주수량</th>
                <th>발주단가</th>
        &lt;#if poInfo.purc_typ == 'MT'&gt;
                <th>납품일자</th>
                <th>검수담당자</th>
        &lt;#else&gt;
                <th>수행시작일</th>
                <th>수행종료일</th>
        &lt;/#if&gt;
                <th>구매그룹</th>
            </tr>
            <tr>
                <th>항번</th>
                <th>규격</th>
                <th>단위</th>
                <th>발주금액</th>
        &lt;#if poInfo.purc_typ == 'MT'&gt;
                <th>납품장소</th>
        &lt;#else&gt;
                <th>수행장소</th>
        &lt;/#if&gt;
                <th>면세여부</th>
                <th>구매의뢰자</th>
            </tr>
&lt;#list previousPoItems as previousPoItem&gt;
            <tr>
                <td rowspan="2">${previousPoItem_index+1}</td>
                <td>${previousPoItem.disp_item_cd?default("")}</td>
                <td class="tl">${previousPoItem.item_nm?default("")}</td>
                <td class="tr">${previousPoItem.item_qty?default(0)}</td>
                <td class="tr">${previousPoItem.item_price?default(0)}</td>
        &lt;#if poInfo.purc_typ == 'MT'&gt;
                <td>${previousPoItem.rd_date[0..3]?default("")}/${previousPoItem.rd_date[4..5]?default("")}/${previousPoItem.rd_date[6..7]?default("")}</td>
                <td>${previousPoItem.gr_chr_nm?default("")} </td>
        &lt;#else&gt;
                <td>${previousPoItem.prd_sd[0..3]?default("")}/${previousPoItem.prd_sd[4..5]?default("")}/${previousPoItem.prd_sd[6..7]?default("")}</td>
                <td>${previousPoItem.prd_ed[0..3]?default("")}/${previousPoItem.prd_ed[4..5]?default("")}/${previousPoItem.prd_ed[6..7]?default("")}</td>
        &lt;/#if&gt;
                <td>${previousPoItem.purc_grp_cd?default("")} ${previousPoItem.purc_grp_nm?default("")}</td>
            </tr>
            <tr>
                <td>${previousPoItem.po_lno?default("")}</td>
                <td class="tl">${previousPoItem.spec?default("")}</td>
                <td>${previousPoItem.unit_cd?default("")}</td>
                <td class="tr">${previousPoItem.item_amt?default(0)}</td>
                <td>${previousPoItem.rd_locat?default("")}</td>
                <td>${previousPoItem.duty_free_yn_str?default("")}</td>
                <td>${previousPoItem.pr_sug_nm?default("")}</td>
            </tr>
&lt;/#list&gt;
        </table>
    </section>
    <section>
        <h3>품목정보 (변경후)<span>통화 : ${poInfo.cur?default("")}</span></h3>
        <table class="tc">
            <colgroup>
                <col style="width:5%" />
                <col style="width:10%" />
                <col style="width:30%" />
                <col style="width:7%" />
                <col style="width:12%" />
                <col style="width:12%" />
                <col style="width:12%" />
                <col style="width:12%" />
            </colgroup>
            <tr>
                <th rowspan="2">순번</th>
                <th>품목코드</th>
                <th>품목명</th>
                <th>발주수량</th>
                <th>발주단가</th>
        &lt;#if poInfo.purc_typ == 'MT'&gt;
                <th>납품일자</th>
                <th>검수담당자</th>
        &lt;#else&gt;
                <th>수행시작일</th>
                <th>수행종료일</th>
        &lt;/#if&gt;
                <th>구매그룹</th>
            </tr>
            <tr>
                <th>항번</th>
                <th>규격</th>
                <th>단위</th>
                <th>발주금액</th>
        &lt;#if poInfo.purc_typ == 'MT'&gt;
                <th>납품장소</th>
        &lt;#else&gt;
                <th>수행장소</th>
        &lt;/#if&gt;
                <th>면세여부</th>
                <th>구매의뢰자</th>
            </tr>
&lt;#list poItems as poItem&gt;
            <tr>
                <td rowspan="2">${poItem_index+1}</td>
                <td>${poItem.disp_item_cd?default("")}</td>
                <td class="tl">${poItem.item_nm?default("")}</td>
                <td class="tr">${poItem.item_qty?default(0)}</td>
                <td class="tr">${poItem.item_price?default(0)}</td>
        &lt;#if poInfo.purc_typ == 'MT'&gt;
                <td>${poItem.rd_date[0..3]?default("")}/${poItem.rd_date[4..5]?default("")}/${poItem.rd_date[6..7]?default("")}</td>
                <td>${poItem.gr_chr_nm?default("")} </td>
        &lt;#else&gt;
                <td>${poItem.prd_sd[0..3]?default("")}/${poItem.prd_sd[4..5]?default("")}/${poItem.prd_sd[6..7]?default("")}</td>
                <td>${poItem.prd_ed[0..3]?default("")}/${poItem.prd_ed[4..5]?default("")}/${poItem.prd_ed[6..7]?default("")}</td>
        &lt;/#if&gt;
                <td>${poItem.purc_grp_cd?default("")} ${poItem.purc_grp_nm?default("")}</td>
            </tr>
            <tr>
                <td>${poItem.po_lno?default("")}</td>
                <td class="tl">${poItem.spec?default("")}</td>
                <td>${poItem.unit_cd?default("")}</td>
                <td class="tr">${poItem.item_amt?default(0)}</td>
                <td>${poItem.rd_locat?default("")}</td>
                <td>${poItem.duty_free_yn_str?default("")}</td>
                <td>${poItem.pr_sug_nm?default("")}</td>
            </tr>
&lt;/#list&gt;
        </table>
    </section>
</article>
```
* LCOPEN	외자LC개설	N
``` html
```
* ESTLG	외자L/G 발급	N
``` html
```