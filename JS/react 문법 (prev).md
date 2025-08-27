```
const handleSkillsChange = (e: ChangeEvent<HTMLInputElement>) => {
    const skillsString = e.target.value;
    const skillsArray = skillsString.split(',').map(skill => skill.trim());
							    // 만들어진 배열의 각 요소(`skill`)를 순회하면서 `trim()` 함수를 적용
    setPortfolio(prev => ({...prev, skills: skillsArray}));
  }
```


1. **`setPortfolio(prev => ({...prev, skills: skillsArray}));`**
    - `setPortfolio`: `useState` 훅에서 `portfolio` 상태를 변경하기 위해 제공하는 함수
    - `prev => ...`: 이전 상태(`prev`)를 기반으로 새로운 상태를 만들 때 사용
    - `{...prev}`: **스프레드 문법(Spread Syntax)**. 기존 `portfolio` 객체(`prev`)의 모든 속성을 그대로 복사하여 새로운 객체를 만듦 **(React의 불변성 유지를 위해 매우 중요)**
    - `skills: skillsArray`: 복사된 새 객체의 `skills` 속성 값을 위에서 만든 `skillsArray`로 덮어쓰거나 새로 추가

