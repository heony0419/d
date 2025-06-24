# 1번문제

1. 요구사항 역분석하기
   - 주사위 숫자만큼 이동하여 도착할 위치를 계산하는 판단 조건과 변수 의미를 정리하여 기록하기
   - nextposition 함수를 확인하면

   
func nextPosition(current: Int, _ dice: Int) -> Int {

    let next = current + dice
    
    if (next == 4) {
    
        return dice + 10
        
    }
    
    else if (next == 8) {
    
        return dice + 22
        
    }
    
    else if (next == 28) {
        return dice + 48
    }
    else if (next == 21) {
        return dice + 42
    }
    else if (next == 50) {
        return dice + 17
    }
    else if (next == 71) {
        return dice + 92
    }
    else if (next == 80) {
        return dice + 19
    }
    
    return dice; 
}

함수 내의 next가 숫자 칸이라고 하였을 때, 해당하는 숫자 칸에 이동을 하면 사다리를 타서 높은 숫자 칸으로 이동한다는 내용이라는 것을 알 수 있다.

예를 들어, next가 4가 되었을 때는, 4에서 10을 더한 14로 사다리를 타서 이동을 하고, 8이 되었을 때에는 8에서 22를 더한 30으로 이동하는 것을 알 수 있다.

위 함수에서 return dice + 00 은 next 값이 사다리를 타는 숫자 칸이 나왔을 때 사다리를 타는 칸에 가게 된 주사위의 숫자와 그 칸에서 얼마나 윗쪽으로 갔는지의 숫자를 더한 값을 반환한다는 의미임을 알 수 있다.

위 함수에서 next가 21이 나왔을 때 return 값을 dice+42가 아닌 dice+21이 되어야한다. 왜냐하면 여기에서 숫자 21은 21에서 42까지 상승을 한 칸 수 즉, 사다리의 끝인 42에서 사다리의 시작인 21의 값을 뺀 21이 적합하다는 것을 알 수 있다.

이와 마찬가지로 next가 71이 나왔을 때는 return 값을 dice+92가 아닌 사다리의 끝인 92와 사다리의 시작인 71을 뺀 21이 더 적합하다는 것을 알 수 있다.


그러므로 위에 있는 코드에서

func nextPosition(current: Int, _ dice: Int) -> Int {

    let next = current + dice
    
    if (next == 4) {
    
        return dice + 10
        
    }
    
    else if (next == 8) {
    
        return dice + 22
        
    }
    
    else if (next == 28) {
    
        return dice + 48
        
    }
    
    else if (next == 21) {
    
        return dice + 21
        
    }
    
    else if (next == 50) {
    
        return dice + 17
        
    }
    
    else if (next == 71) {
    
        return dice + 21
        
    }
    
    else if (next == 80) {
    
        return dice + 19
        
    }
    

   
    return dice;
    
}
로 바뀌어야한다.

위 내용으로 바꾸었을 때에는 정상적으로 사다리가 알맞게 작동을 한다.


참고로 맨 마지막 줄에 있는 return dice; 는 주사위를 던졌는데 사다리를 타지 못하였을 때의 경우이고, 이때에는 특수한 경우가 아니므로 주사위의 값만 반환한다는 것을 알 수 있다.




2. 새로운 요구사항 추가하기
   - 뱀 동작이 생겼을 때

기존의 코드에서는 시작하는 위치에서 주사위 값을 설정을 하고, nextFunction이라는 함수를 통해서 주사위의 칸 만큼 이동, 도착한 칸이 사다리의 시작지점이라면 끝지점으로 이동을 하여 시작하는 위치를 다시 재설정하였다.
이 코드에서 nextFunction이라는 코드를 활용하여 이동을 완료한 위치가 뱀의 시작 위치인지 아닌지를 판단하는 nextPosition2 함수를 만들었다. 말 그대로 도착한 위치가 뱀의 시작 부분인지 아닌지를 판단하고 시작 부분이라면 내려가는 위치로 이동을 하고, 그것이 아니면 그 자리 그대로 위치하는 코드를 만들었다.
nextPosition2를 실행한 결과를 next2라는 변수에 저장을 하고, 이를 다시 next 값에 반영을 하여 주사위를 돌렸을 때의 최종위치를 결정하였다.
