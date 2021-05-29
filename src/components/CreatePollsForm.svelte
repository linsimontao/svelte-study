<script>
    import Button from '../shared/Button.svelte';
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();
    let field = {
        question: '',
        answerA: '',
        answerB: ''
    };
    let errors = {
        question: '',
        answerA: '',
        answerB: ''
    };
    let valid = false;

    const submitHandler = () => {
        valid = true;
        
        if (field.question.trim().length < 5) {
            valid = false;
            errors.question = 'Question must longer than 5';
        } else {
            errors.question = '';
        }

        if (field.answerA.trim().length < 1) {
            valid = false;
            errors.answerA = 'AnswerA must longer than 1';
        } else {
            errors.answerA = '';
        }

        if (field.answerB.trim().length < 1) {
            valid = false;
            errors.answerB = 'AnswerB must longer than 1';
        } else {
            errors.answerB = '';
        }

        if (valid) {
            const poll = {
                ...field,
                voteA: 0,
                voteB: 0,
                id: Math.random()
            }
            dispatch('PollCreate', poll);
        }
    };
</script>

<form on:submit|preventDefault={submitHandler} >
    <div class="form-field">
        <label for="question">Poll question:</label>
        <input type="text" id="question" bind:value={field.question}>
        <div class="error">{errors.question}</div>
    </div>
    <div class="form-field">
        <label for="answer-a">Answer A:</label>
        <input type="text" id="answer-a" bind:value={field.answerA}>
        <div class="error">{errors.answerA}</div>
    </div>
    <div class="form-field">
        <label for="answer-b">Answer B:</label>
        <input type="text" id="answer-b" bind:value={field.answerB}>
        <div class="error">{errors.answerB}</div>
    </div>
    <Button type="secondary" flat={true}>Add Poll</Button>
</form>

<style>
    form {
        width: 400px;
        margin: 0 auto;
        text-align: center;
    }

    .form-field {
        margin: 18px auto;
    }
    input {
        width: 100%;
        border-radius: 6px;
    }
    label {
        margin: 10px auto;
        text-align: left;
    }
    .error {
        color: #d91b42;
        font-weight: bold;
        font-size: 12px;
    }
</style>