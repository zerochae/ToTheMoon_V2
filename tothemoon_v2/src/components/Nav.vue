<template>
  <div class="nav-warpper">
    <transition name="fade">
      <div class="nav" v-if="this.showMenu == true">
        <div class="bg-black">
          <div class="bg-white">
            <div class="nav-hidden-menu">
              <div class="nav-menu">
                <ul>
                  <h3>거래소</h3>
                  <li>거래</li>
                  <li>주문/거래 현황</li>
                  <li>투자유의 지정 안내</li>
                </ul>
              </div>
              <div class="nav-menu">
                <ul>
                  <h3>빗썸캐시</h3>
                  <li>빗썸캐시란?</li>
                  <li>빗썸캐시 송금</li>
                </ul>

                <ul>
                  <h3>빗썸캐시몰</h3>
                  <li>신세계면세점</li>
                  <li>Qoo10</li>
                  <li>인터파크 비즈마켓</li>
                  <li>상품권몰</li>
                </ul>
              </div>

              <div class="nav-menu">
                <ul>
                  <h3>상품•서비스</h3>
                  <li>오토 트레이딩</li>
                  <li>BTC 오픈</li>
                  <li>스테이킹</li>
                  <li>이더리움 2.0 스테이킹</li>
                  <li>빗썸프라임</li>
                  <li>정액쿠폰</li>
                  <li>로그인 도용방지</li>
                  <li>빗썸카페</li>
                  <li>빗썸지수</li>
                </ul>
              </div>

              <div class="nav-menu">
                <ul>
                  <h3>제휴•입점</h3>
                  <li>상승장 렌딩</li>
                  <li>하락장 렌딩</li>
                  <li>예치</li>
                  <li>자동매매(봇)</li>
                </ul>
              </div>

              <div class="nav-menu">
                <ul>
                  <h3>지갑관리</h3>
                  <li>자산현황</li>
                  <li>입금</li>
                  <li>출금</li>
                  <li>거래내역</li>
                  <li>입출금현황</li>
                </ul>
              </div>

              <div class="nav-menu">
                <ul>
                  <h3>계정관리</h3>
                  <li>회원정보 관리</li>
                  <li>인증센터</li>
                  <li>API관리</li>
                  <li>온라인송금 API</li>
                  <li>이벤트쿠폰</li>
                </ul>

                <ul>
                  <h3>설정</h3>
                  <li>보안센터</li>
                  <li>알림설정</li>
                  <li>빗썸캐시 설정</li>
                </ul>
              </div>

              <div class="nav-menu">
                <ul>
                  <h3>고객지원</h3>
                  <li>공지사항</li>
                  <li>고객학원 제도 안내</li>
                  <li>이용안내</li>
                  <li>1:1문의하기</li>
                  <li>수수료 안내</li>
                  <li>증빙센터</li>
                  <li>상품권 환불</li>
                  <li>API Docs</li>
                  <li>상장 안내</li>
                </ul>
              </div>
              <button class="menu-close-btn" @click="this.showMenu = false">
                <i class="fas fa-times"></i>
              </button>
            </div>
          </div>
        </div>
      </div>
    </transition>
    <div class="header">
      <div class="sub-menu">
        <button>거래소</button>
        <button>빗썸캐시</button>
        <button>상품•서비스</button>
        <button>제휴•입점</button>
        <i @click="this.showMenu = true" class="fas fa-bars"></i>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showMenu: false,
    };
  },
};
</script>

<style>
@import "./../assets/Nav.css";
</style>