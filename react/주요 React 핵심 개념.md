
| **useState** (압도적 1위)                              | 컴포넌트가 값을 "기억"하고, 값이 바뀌면 화면을 다시 그림. `const [값, set값] = useState(초기값)` |
| -------------------------------------------------- | -------------------------------------------------------------------- |
| **이벤트 핸들러** (`onPress`/`onChangeText`)             | 탭/입력 시 실행되는 함수. 웹의 `onClick`에 해당                                     |
| **조건부 렌더링** (`&&`, `? :`)                          | 상태에 따라 UI를 보이거나 숨김. `loading && <Spinner/>`                          |
| **JSX / 기본 부품** (`View`/`Text`/`TouchableOpacity`) | HTML처럼 생긴 문법. `View`=박스, `Text`=글자, `TouchableOpacity`=버튼            |
| **useEffect**                                      | 화면이 뜬 후 실행되는 부수효과(API 호출 등). 의존성 배열 `[]`로 실행 시점 제어                   |
| **리스트 렌더링** (`.map`, `FlatList`)                   | 배열을 화면 항목들로 변환. `key`가 필수                                            |
| **StyleSheet.create()**                            | CSS 파일 대신 JS 객체로 스타일. 단위 없는 숫자(`padding: 16`), camelCase             |
| **async / await**                                  | API·저장 같은 비동기 작업을 순서대로 기다림                                           |
| **커스텀 훅** (`use...`)                               | 재사용 로직을 `use`로 시작하는 함수로 추출                                           |
| **Context API** (`createContext`+`useContext`)     | props 없이 앱 전역에서 값 공유                                                 |
| **useRouter / useLocalSearchParams**               | 화면 이동·동적 주소 값 읽기 (Expo Router 전용)                                    |
| **Props** (함수 매개변수)                                | 부모 → 자식으로 내려주는 데이터                                                   |
| **useCallback / useMemo / useRef**                 | 성능 최적화 훅(함수·계산 결과 기억, 재렌더 없이 값 유지)                                   |
| **AsyncStorage**                                   | 기기에 데이터 영구 저장(로그인 유지 등)                                              |
